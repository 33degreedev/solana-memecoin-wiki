---
title: "Migration Speed Detector — Canonical Architecture"
name: Migration Speed Detector — Canonical Architecture
type: framework
tags: [framework, system-design]
---

# Migration Speed Detector — Canonical Architecture

**Status:** Design validated with chloe (EXTREME, $1.68M ATH) and embers (MODERATE, $6.93K winner).
**Replaces:** Migration_Speed_Detector_System.md, Migration_Speed_Detector_Implementation.md

---

## What It Does

Polls pump.fun every 30 seconds for newly migrated tokens. When a token graduates from
the bonding curve fast enough AND a known trader wallet was in the BC pool, it fires an
alert to your phone with entry guidance, position size, and one-click links.

---

## Signal Hierarchy

```
PRIMARY ──── Migration Speed
             Time from BC pool creation → graduation ($69K MC threshold)
             Faster = more concentrated organic demand = higher ceiling
             Objective and on-chain — no interpretation required.

SECONDARY ── Known Trader Presence
             Was a proven wallet in the bonding curve before migration?
             Validates demand is real (not a bot farm or dev pump).
             Operates as a binary gate: ≥1 known wallet = pass.

OUTPUT ───── Entry Tier
             Speed + validation → position size + timing.
             Size scales with confidence. Timing scales with urgency.
```

---

## Alert Tier Matrix

| Tier       | BC Fill Time  | Alert? | Entry Timing    | Position  | Confidence    |
|------------|---------------|--------|-----------------|-----------|---------------|
| EXTREME    | < 90s         | ✅ YES  | t=0 at migration| 0.25 SOL  | Max           |
| VERY_FAST  | 90s – 3min    | ✅ YES  | t=0 at migration| 0.20 SOL  | High          |
| FAST       | 3 – 5min      | ✅ YES  | t=0 at migration| 0.15 SOL  | Medium-High   |
| MODERATE   | 5 – 10min     | ✅ YES  | t=45s post-mig  | 0.12 SOL  | Medium        |
| SLOW       | 10 – 30min    | ❌ SKIP | —               | —         | Too slow      |
| STALLED    | > 30min       | ❌ SKIP | —               | —         | Dead          |

**Key rule:** MODERATE still alerts when known traders are present (embers = 23min MODERATE, still won).
SLOW and STALLED are hard-skips regardless of traders.

Stop loss: **-15%** on all tiers.
Exit targets: **+5% (exit 50%)** → **+10% (exit remaining 50%)**.
Timer: **60 seconds** from entry, exit at market if targets not hit.

---

## System Architecture

```
╔═══════════════════════════════════════════════════════════════╗
║                        DATA SOURCES                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ┌─────────────────────┐     ┌─────────────────────┐         ║
║  │  pump.fun API       │     │  Birdeye API         │         ║
║  │  (unofficial)       │     │  (fallback only)     │         ║
║  │  Poll: every 30s    │     │  /defi/token_listing │         ║
║  │  Filter: migrated   │     │                      │         ║
║  │  Window: last 5min  │     │                      │         ║
║  └──────────┬──────────┘     └──────────┬───────────┘         ║
║             └──────────────┬────────────┘                     ║
║                            ▼                                  ║
║             ┌──────────────────────────┐                      ║
║             │  Migrated Token Record   │                      ║
║             │  ca, name                │                      ║
║             │  created_at (ISO UTC)    │                      ║
║             │  migrated_at (ISO UTC)   │                      ║
║             │  bc_pool (BC address)    │                      ║
║             └──────────────┬───────────┘                      ║
╚════════════════════════════╪══════════════════════════════════╝
                             │
                             ▼
╔═══════════════════════════════════════════════════════════════╗
║                     PROCESSING PIPELINE                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ┌─────────────────────────────────────────────────────────┐  ║
║  │ GATE 0 — Dedup                                          │  ║
║  │ Is this CA already in ALERT_CACHE?                      │  ║
║  │ YES → skip   NO → continue                              │  ║
║  └─────────────────────┬───────────────────────────────────┘  ║
║                        │                                      ║
║  ┌─────────────────────▼───────────────────────────────────┐  ║
║  │ STEP 1 — Calculate Migration Time                       │  ║
║  │ migration_sec = (migrated_at - created_at).seconds      │  ║
║  └─────────────────────┬───────────────────────────────────┘  ║
║                        │                                      ║
║  ┌─────────────────────▼───────────────────────────────────┐  ║
║  │ STEP 2 — Classify Speed Tier                            │  ║
║  │ < 90s      → EXTREME                                    │  ║
║  │ < 180s     → VERY_FAST                                  │  ║
║  │ < 300s     → FAST                                       │  ║
║  │ < 600s     → MODERATE                                   │  ║
║  │ < 1800s    → SLOW     ← hard skip                       │  ║
║  │ ≥ 1800s    → STALLED  ← hard skip                       │  ║
║  └─────────────────────┬───────────────────────────────────┘  ║
║                        │                                      ║
║  ┌─────────────────────▼───────────────────────────────────┐  ║
║  │ GATE 1 — Speed Filter                                   │  ║
║  │ tier ∈ {SLOW, STALLED}? → DISCARD                       │  ║
║  │ tier ∈ {EXTREME, VERY_FAST, FAST, MODERATE}? → continue │  ║
║  └─────────────────────┬───────────────────────────────────┘  ║
║                        │                                      ║
║  ┌─────────────────────▼───────────────────────────────────┐  ║
║  │ STEP 3 — Query BC Pool Transactions (Solscan)           │  ║
║  │                                                         │  ║
║  │ ⚠ Query bc_pool address, NOT the pumpAMM pool.          │  ║
║  │   bc_pool = bonding curve pool (pre-migration)          │  ║
║  │   pumpAMM = post-migration trading pool (different)     │  ║
║  │                                                         │  ║
║  │ GET Solscan defi/activities for bc_pool                 │  ║
║  │ Filter: ACTIVITY_TOKEN_SWAP only                        │  ║
║  │ Time range: created_at → migrated_at                    │  ║
║  │ Extract: buyer wallet, sol_amount, timestamp            │  ║
║  └─────────────────────┬───────────────────────────────────┘  ║
║                        │                                      ║
║  ┌─────────────────────▼───────────────────────────────────┐  ║
║  │ GATE 2 — Known Trader Validation                        │  ║
║  │ For each txn: is buyer in KNOWN_TRADERS?                │  ║
║  │             AND amount ≥ trader.min_buy?                │  ║
║  │ 0 matches → DISCARD                                     │  ║
║  │ ≥1 match  → ALERT                                       │  ║
║  └─────────────────────┬───────────────────────────────────┘  ║
║                        │                                      ║
╚════════════════════════╪══════════════════════════════════════╝
                         │
                         ▼
╔═══════════════════════════════════════════════════════════════╗
║                       OUTPUT LAYER                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ┌─────────────────────────────────────────────────────────┐  ║
║  │ Build Alert Payload                                     │  ║
║  │  token_name, ca, migration_sec, tier                    │  ║
║  │  traders_found[], entry_timing, position_size           │  ║
║  │  stop_loss, targets                                     │  ║
║  │  links: Axiom, Solscan, DexScreener                     │  ║
║  └─────────────────────┬───────────────────────────────────┘  ║
║                        │                                      ║
║              ┌─────────┴──────────┐                           ║
║              │                   │                            ║
║       ┌──────▼──────┐    ┌───────▼──────┐                    ║
║       │  Telegram   │    │   Discord    │  ← Phase 2          ║
║       │  Bot (MVP)  │    │   Webhook    │                     ║
║       └──────┬──────┘    └──────────────┘                    ║
║              │                                                ║
║              ▼                                                ║
║       ┌─────────────┐                                         ║
║       │  YOUR PHONE │                                         ║
║       └─────────────┘                                         ║
║                                                               ║
║  DEDUP: Add CA → ALERT_CACHE with timestamp + tier            ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## API Stack

### Layer 1 — Migration Feed

**pump.fun (primary, unofficial):**
```
Base: https://frontend-api.pump.fun
Endpoint: /coins?offset=0&limit=50&sort=last_trade_unix_timestamp&order=DESC

Fields needed:
  mint              → CA (token address)
  name              → token name
  created_timestamp → pool creation (Unix ms)
  raydium_pool      → non-null = migrated to pumpAMM
  king_of_the_hill_timestamp → migration timestamp (Unix ms)
  bonding_curve     → BC pool address (for Solscan query)

Filter logic:
  raydium_pool IS NOT NULL   (has migrated)
  AND king_of_the_hill_timestamp ≥ (now - 5min)  (recently migrated)
  AND mint NOT IN ALERT_CACHE  (not already alerted)
```

**Birdeye (fallback):**
```
Base: https://public-api.birdeye.so
Endpoint: /defi/v3/token/new-listing?sort_by=created_time&sort_type=desc&limit=50
Header: X-API-KEY: {BIRDEYE_API_KEY}

Limitation: Migration timestamps may lag 60-90s vs pump.fun direct
```

### Layer 2 — BC Pool Validation

**Solscan (defi activities):**
```
Base: https://pro-api.solscan.io/v2.0
Endpoint: /account/defi/activities

Params:
  address        = bc_pool address (bonding_curve field from pump.fun)
  activity_type  = ACTIVITY_TOKEN_SWAP
  block_time_gt  = created_at (Unix seconds)
  block_time_lt  = migrated_at (Unix seconds)
  page_size      = 100
  sort_by        = block_time
  sort_order     = asc

Response fields:
  routers[].amount1  → SOL in (buyer amount)
  routers[].account2 → buyer wallet address
  block_time         → Unix timestamp

Rate limit: ~1 req/sec (free tier). Budget: 1 call per filtered token.
```

### Layer 3 — Alert Delivery

**Telegram (MVP):**
```
POST https://api.telegram.org/bot{TOKEN}/sendMessage
Body: { chat_id, text, parse_mode: "Markdown", disable_web_page_preview: true }
```

---

## Known Traders Registry

```python
KNOWN_TRADERS = {
    # wallet_address → trader config
    "4BdKaxN8G6ka4GYtQQWk4G4dZRUTX2vQH9GcXdBREFUk": {
        "name": "theo",
        "tier": "S",
        "min_buy_sol": 0.5,
    },
    "G6fUXjMKPJzCY1rveAE6Qm7wy5U3vZgKDJmN1VPAdiZC": {
        "name": "clukzsol",
        "tier": "S",
        "min_buy_sol": 0.5,
    },
    # Add more via Axiom top traders panel → copy wallet address
    # Format: wallet_str → { name, tier, min_buy_sol }
}

MIN_BUY_DEFAULT = 0.3  # SOL — floor for unknown tier traders
```

**How to expand:** Open any winning coin on Axiom → Top Traders panel → identify wallets
that appear repeatedly across winners → add to registry.

---

## Implementation (Clean Pseudocode)

```python
import time
from datetime import datetime, timezone

ALERT_CACHE = {}  # { ca: { alerted_at, tier, trader_count } }
SLOW_TIERS = {"SLOW", "STALLED"}
POLL_INTERVAL_SEC = 30


def run():
    while True:
        try:
            process_cycle()
        except Exception as e:
            log_error(e)
        time.sleep(POLL_INTERVAL_SEC)


def process_cycle():
    tokens = fetch_migrated_tokens(since_minutes=5)

    for token in tokens:
        # ── GATE 0: Dedup ──────────────────────────────────────
        if token.ca in ALERT_CACHE:
            continue

        # ── STEP 1: Migration time ─────────────────────────────
        migration_sec = (token.migrated_at - token.created_at).total_seconds()

        # ── STEP 2: Tier ───────────────────────────────────────
        tier = classify_tier(migration_sec)

        # ── GATE 1: Speed filter ───────────────────────────────
        if tier in SLOW_TIERS:
            continue

        # ── STEP 3: Solscan BC pool query ─────────────────────
        bc_txns = fetch_bc_transactions(
            bc_pool=token.bc_pool,
            start=token.created_at,
            end=token.migrated_at,
        )

        # ── GATE 2: Known trader validation ────────────────────
        traders_found = match_known_traders(bc_txns)
        if not traders_found:
            continue

        # ── FIRE ALERT ────────────────────────────────────────
        payload = build_payload(token, migration_sec, tier, traders_found)
        send_telegram(payload)

        ALERT_CACHE[token.ca] = {
            "alerted_at": datetime.now(timezone.utc),
            "tier": tier,
            "trader_count": len(traders_found),
        }


def classify_tier(migration_sec: float) -> str:
    if migration_sec < 90:    return "EXTREME"
    if migration_sec < 180:   return "VERY_FAST"
    if migration_sec < 300:   return "FAST"
    if migration_sec < 600:   return "MODERATE"
    if migration_sec < 1800:  return "SLOW"
    return "STALLED"


def match_known_traders(txns: list) -> list:
    matched = []
    for txn in txns:
        trader = KNOWN_TRADERS.get(txn.buyer_wallet)
        if trader and txn.sol_amount >= trader["min_buy_sol"]:
            matched.append({
                "name": trader["name"],
                "wallet": txn.buyer_wallet,
                "buy_sol": txn.sol_amount,
                "time": txn.timestamp,
            })
    return matched


ENTRY_TIMING = {
    "EXTREME":   "t=0 (enter at migration)",
    "VERY_FAST": "t=0 (enter at migration)",
    "FAST":      "t=0 (enter at migration)",
    "MODERATE":  "t=45s (wait for post-migration absorption)",
}

POSITION_SIZE = {
    "EXTREME":   0.25,
    "VERY_FAST": 0.20,
    "FAST":      0.15,
    "MODERATE":  0.12,
}


def build_payload(token, migration_sec, tier, traders_found) -> dict:
    mins, secs = divmod(int(migration_sec), 60)
    return {
        "token": {"name": token.name, "ca": token.ca},
        "migration": {
            "time": f"{mins}m {secs}s",
            "tier": tier,
        },
        "traders": traders_found,
        "entry": {
            "timing":   ENTRY_TIMING[tier],
            "size_sol": POSITION_SIZE[tier],
            "stop":     "-15%",
            "targets":  ["+5% (50%)", "+10% (50%)"],
            "timer":    "60s",
        },
        "links": {
            "axiom":       f"https://axiom.trade/meme/{token.ca}",
            "dexscreener": f"https://dexscreener.com/solana/{token.ca}",
            "solscan":     f"https://solscan.io/account/{token.bc_pool}",
        },
    }
```

---

## Alert Message Format (Telegram)

```
⚡ EXTREME MIGRATION — chloe

CA: 2ra5idcz...pump
BC fill time: 1m 16s
Tier: EXTREME

Traders in BC:
  • clukzsol  →  2.36 SOL  @  03:10:16

Entry: NOW (t=0)
Size: 0.25 SOL
Stop: -15% | Targets: +5% (50%), +10% (50%)
Timer: 60 seconds from entry

Axiom: https://axiom.trade/meme/2ra5...
DexScreener: https://dexscreener.com/solana/2ra5...
Solscan BC: https://solscan.io/account/7oCe5...
```

---

## Error Handling

```
pump.fun API fails
  └─ catch HTTPError/Timeout → switch to Birdeye fallback
  └─ if Birdeye also fails → log, sleep 60s, retry

Solscan query fails
  ├─ Timeout (>5s) → skip this token this cycle, retry next poll
  └─ 429 Rate Limit → exponential backoff: wait 60s, then 120s

No known traders found
  └─ discard silently (expected, not an error)

Duplicate CA in cache
  └─ skip silently

Telegram send fails
  └─ retry 3x with 5s delays → log failure after 3rd miss
```

---

## Data Flow Timeline (Chloe Example)

```
03:09:00 UTC  Nikita Bier tweets pig video → narrative fires
03:10:16 UTC  BC pool created + immediately fills (49 snipers in first second)
              migration_time = 76 seconds → EXTREME tier

──────────────── YOUR DETECTOR ────────────────

03:10:30 UTC  30s poll fires → pump.fun returns chloe as migrated
03:10:30 UTC  Gate 0: CA not in cache → continue
03:10:30 UTC  migration_sec = 76 → tier = EXTREME
03:10:30 UTC  Gate 1: EXTREME ≠ SLOW → continue
03:10:31 UTC  Solscan query: BC pool 7oCe5... → 49 swap txns
03:10:32 UTC  Gate 2: clukzsol matched (2.36 SOL ≥ 0.5 min) → FIRE
03:10:32 UTC  Telegram: "⚡ EXTREME — chloe | 1m 16s | clukzsol in"

──────────────── YOU ────────────────

03:10:33 UTC  Alert arrives on phone (~1s Telegram delivery)
03:10:35 UTC  You click Axiom link → chart opens
03:11:01 UTC  t=45s post-migration: you enter 0.25 SOL
              (note: EXTREME = t=0 entry, so this is a late entry)
03:12:01 UTC  60s timer expires → exit at market
              ATH reached $1.68M hours later
```

**Total system latency: ~32 seconds from migration to alert on phone.**

---

## Build Phases

### Phase 1 — MVP (2 hours)
- [ ] pump.fun polling loop with 30s interval
- [ ] Migration time calculation + tier classification
- [ ] Solscan BC pool query + known trader matching
- [ ] ALERT_CACHE dedup
- [ ] Telegram message formatting + delivery
- [ ] Manual backtest: run against chloe, embers, AIB timestamps

### Phase 2 — Hardening (Day 2-3)
- [ ] Birdeye fallback when pump.fun is down
- [ ] Solscan rate limit handling (exponential backoff)
- [ ] Persistent ALERT_CACHE (file or SQLite, survives restart)
- [ ] Logging: every alert fired + every discard reason
- [ ] Discord webhook as second delivery channel

### Phase 3 — Live Calibration (Week 1)
- [ ] Run live for 5 days, log all alerts
- [ ] For each alert: track entry price, ATH, outcome
- [ ] Measure false positive rate (alert fired, coin died)
- [ ] Tune min_buy_sol thresholds if too noisy
- [ ] Expand KNOWN_TRADERS from Axiom panels on winning coins

### Phase 4 — Enhancement (Week 2+)
- [ ] RPC event listener (sub-10s latency instead of ±30s)
- [ ] Narrative score integration (from Winner Checklist)
- [ ] Dynamic position sizing: (speed_tier × narrative_score) composite
- [ ] Auto-execute webhook (optional, high-risk)

---

## Success Metrics (After 1 Week Live)

| Metric              | Target              | Notes                          |
|---------------------|---------------------|--------------------------------|
| Alerts / day        | 2–4                 | Under = too restrictive        |
| Alert latency       | < 60s from migration| Enough for t=0 or t=45s entry  |
| False positive rate | < 20%               | Token runs for <5min then dies |
| True positive rate  | > 60%               | Alert + coin runs 5%+          |
| Missed trades       | < 2/week            | FAST+ coins we didn't catch    |

---

## Related

- [[patterns/migration-speed-signal]] — Tier thresholds + case study validation
- [[playbooks/migration-alert]] — What to do when alert fires
- [[coins/chloe]] — Validated EXTREME tier example
- [[coins/embers]] — Validated MODERATE tier example
- [[traders/theo]] — Known trader profile
