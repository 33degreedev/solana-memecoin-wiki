---
title: "Migration Detector — How It Works"
name: Migration Detector — How It Works
description: Full technical breakdown of the bot's monitoring system, detection paths, tier thresholds, and known gaps. Includes the Make A Wish missed-alert investigation (Apr 29, 2026).
type: framework
status: complete
tags: [bot, architecture, detection, alerts, debugging]
---

# Migration Detector — How It Works

## Architecture Overview

The bot runs a **WebSocket connection to PumpPortal** (`pumpportal.fun`) listening for two event types:

1. **Migration events** — any pump.fun token that graduates from bonding curve to pumpAMM
2. **Account trade events** — buys/sells from the 24 tracked trader wallets

All processing is event-driven. No polling. The bot reacts in real-time to migrations and trader activity.

---

## Speed Tier Classification

When a migration fires, the bot calculates how long the bonding curve took to fill (time from token creation to migration). This determines the speed tier:

| Tier | BC Fill Time | Alert | Description |
|---|---|---|---|
| EXTREME | 0 – 90s | ✅ ON | Bot battles, massive demand |
| VERY_FAST | 90s – 3min | ✅ ON | Strong organic + bot demand |
| FAST | 3 – 5min | ✅ ON | Solid demand, some narrative |
| MODERATE | 5 – 10min | ✅ ON | Mixed demand |
| MID | 10 – 15min | ✅ ON | Slower fill, conviction plays |
| SLOW | 15 – 20min | ✅ ON | Low speed, filter carefully |
| STALLED | 20min+ | ❌ SKIP | Too slow — pre-watch only |

---

## Three Detection Paths

### Path A — Pre-Watch (any tier, no time limit)

**How it works:** The bot monitors all 24 tracked wallets in real-time via the PumpPortal WebSocket. When a tracked wallet buys a token that **hasn't migrated yet**, the bot stores it in the `BC_PRE_WATCHLIST`. When the migration event fires, the bot checks the pre-watchlist FIRST — if found, it alerts immediately.

**Key properties:**
- Alerts on **ANY tier** including SLOW and STALLED — no speed filter
- Skips the Helius RPC scan entirely (no 413 risk)
- Aggregates multiple tracked wallets if several buy the same BC
- Pre-watch entries expire after 2 hours if the token never migrates

**This is how SLOW/STALLED winners get caught.** chadhouse (SLOW, $110K) and Frok (STALLED, $83K) were both pre-watch hits on Apr 29 — tracked wallets were accumulating in BC before migration.

---

### Path A — Migration-Time RPC Scan (under 10 minutes only)

**How it works:** When a migration fires and there's no pre-watch hit, the bot checks the speed tier. If the tier is NOT in `SKIP_TIERS` (SLOW, STALLED), it queries the Helius RPC to fetch all bonding curve transactions, then matches them against the 24 known wallets.

**Tier filter:**

| Tier | RPC Scan? |
|---|---|
| EXTREME | ✅ Scans BC for traders |
| VERY_FAST | ✅ Scans BC for traders |
| FAST | ✅ Scans BC for traders |
| MODERATE | ✅ Scans BC for traders |
| SLOW | ❌ Skipped — `SKIP_TIERS` |
| STALLED | ❌ Skipped — `SKIP_TIERS` |

**RPC scan flow:**
1. Paginate `getSignaturesForAddress` on the BC pool (100 per page)
2. Filter signatures to only the BC time window (creation → migration)
3. Batch-fetch full transactions via `getTransaction` (20 per batch)
4. Parse each transaction for buyer wallet and SOL spent
5. Match against 24 known wallets with min_buy_sol threshold (0.5 SOL)
6. If match found → fire Telegram alert

**Known vulnerability:** The Helius RPC returns `413 Payload Too Large` on pools with heavy activity. On Apr 29, **113 out of 359 migrations (31%) failed the RPC scan** due to this error. The bot silently falls through and adds the token to the Path B watchlist instead — but if the pre-watch also missed the traders, the alert never fires.

---

### Path B — Post-Migration Watch (under 5 minutes only)

**How it works:** If the migration-time scan finds **zero** known traders AND the token migrated in under 5 minutes, the token goes on a 15-minute watchlist. If any tracked wallet buys it post-migration during that window, a Path B alert fires (yellow "POST-MIGRATION BUY" format in Telegram).

**Threshold:** `PATH_B_FAST_THRESHOLD = 300` (5 minutes)

| Tier | Path B Eligible? |
|---|---|
| EXTREME | ✅ Watchlisted for 15 min |
| VERY_FAST | ✅ Watchlisted for 15 min |
| FAST | ✅ Watchlisted for 15 min |
| MODERATE | ❌ Not watchlisted |
| SLOW | ❌ Not watchlisted |
| STALLED | ❌ Not watchlisted |

**Path B recovery:** If the bot receives a trade event for a known trader buying an unknown token (one where the migration event was missed — WebSocket reconnect, etc.), it checks pump.fun to see if the token already migrated. If it migrated within the last 15 minutes (`PATH_B_RECOVERY_MAX_AGE = 900`), it fires a recovery alert.

---

## Alert Decision Summary

| Scenario | Alert? |
|---|---|
| Tracked wallet bought in BC before migration (any speed) | ✅ Always |
| Migration under 10min + tracked wallet found in BC via RPC | ✅ Yes |
| Migration under 5min + no BC traders + tracked wallet buys post-migration | ✅ Yes (Path B) |
| Migration 10–30min (SLOW) + no pre-watch | ❌ Skipped |
| Migration 30min+ (STALLED) + no pre-watch | ❌ Skipped |
| Migration under 10min + RPC scan hits 413 error + no pre-watch | ❌ **Silently missed** |

---

## Known Traders Registry

24 wallets tracked, all Tier S, minimum buy threshold 0.5 SOL:

theo, jijo, clukzsol, west, decu, leck, xander, trenchman, mercy, parsiix, boomer, radiance, bandit, chester, limbork, js shock, dv, nosa1x, nach, kevnszn, euris, errol, nyhrox, solscrow

---

## Alert Format

**Path A (pre-migration trader found):**
```
⚡⚡⚡ EXTREME MIGRATION — $TICKER — TokenName

CA: <contract address>
🕐 Migrated: 11:01:54 AM PT  |  MC: $33.2K
BC fill: 1m 22s  |  Tier: EXTREME

Traders in BC: 3
  • dv → 1.48 SOL @ $12.5K
  • chester → 2.54 SOL @ $15.1K
  • theo → 4.94 SOL @ $18.2K

Entry: t=0 (enter at migration)  |  Size: 0.25 SOL
Stop: -15%  |  Targets: +5% (50%), +10% (50%)
Timer: 60s

DexScreener | Solscan
```

**Path B (post-migration buy):**
```
🟡 POST-MIGRATION BUY — $TICKER — TokenName

CA: <contract address>
🕐 Migrated: 11:01:54 AM PT  (1m 22s, EXTREME)
👤 dv entered +45s after migration  |  MC: $45.2K
💰 1.48 SOL

DexScreener | Solscan
```

---

## Position Sizing (per alert)

| Tier | Suggested Size | Entry Timing |
|---|---|---|
| EXTREME | 0.25 SOL | t=0 (at migration) |
| VERY_FAST | 0.20 SOL | t=0 |
| FAST | 0.15 SOL | t=0 |
| MODERATE | 0.12 SOL | t=45s (wait for absorption) |
| SLOW | 0.10 SOL | t=60s |
| STALLED | 0.10 SOL | t=60s |

Exit config: Stop loss -15%, targets +5% (50%) and +10% (50%), 60s timer.

---

## Known Bugs & Gaps

### 1. Helius RPC 413 Error (Critical)

**Impact:** 31% of migrations fail the BC scan silently.
**Cause:** `getSignaturesForAddress` or batch `getTransaction` returns `413 Payload Too Large` on pools with heavy transaction volume.
**Result:** Bot falls through to Path B watchlist but if no pre-watch hit exists, the alert never fires.
**Status:** Unpatched. See the Make A Wish investigation at the bottom of this page.

**Fix options:**
1. Reduce `PAGE_SIZE` from 100 to 25
2. Add 413-specific retry with exponentially smaller batches
3. Cap scan to last 200 signatures only (known traders typically buy late in BC)

### 2. SLOW/STALLED Skip (By Design)

SLOW and STALLED tokens are excluded from the migration-time RPC scan (`SKIP_TIERS`). They can only be caught by pre-watch. If a tracked wallet buys a SLOW BC but the WebSocket misses the trade event, the token is invisible.

**Mitigation:** The pre-watch system handles this well — Bork ($186K, STALLED) and chadhouse ($110K, SLOW) were both caught. But it's not 100% — WebSocket disconnects during the BC window create blind spots.

### 3. Path B Only Watches Under 5 Minutes

Tokens migrating in 5–10 minutes (MODERATE) don't get Path B watchlisted. If the RPC scan fails (413) on a MODERATE token and no pre-watch exists, there's no fallback.

---

## Make A Wish — Missed Alert Investigation (Apr 29, 2026)

**Token:** Make A Wish ($Wish)
**CA:** `2ssMotVbTUfRJev2UnibHzHsoeszPzgwbfsTZPSHpump`
**Outcome:** $2.1M market cap, $10.5M volume, +6089% — massive runner
**Alert:** ❌ Never fired

### What Happened

1. **Bot saw the migration** at 18:01:54 UTC — classified as **VERY_FAST** (1m 55s)
2. **RPC scan failed** — `413 Client Error: Payload Too Large` on BC pool `DQ9pNYh3qUu1...`
3. **No pre-watch hit** — none of the 24 tracked wallets were detected buying in BC before migration
4. **Path B watchlist seeded** — token was added to the watchlist (10 tokens watching at the time)
5. **No tracked wallet bought post-migration** within the 15-minute Path B window
6. **Result:** Token went to $2.1M with zero alerts

### Root Cause

Two independent failures:

**Failure 1 — RPC 413:** The bonding curve pool had too many transactions for Helius to return. The bot's `fetch_bc_transactions_rpc` function caught the exception and returned an empty list. This is a known bug affecting 31% of all migrations on Apr 29 (113/359).

**Failure 2 — No tracked wallet in BC (probable):** The pre-watch system didn't detect any of the 24 tracked wallets buying Make A Wish before migration. This means either:
- No tracked wallets were actually in the BC (the pump was driven by unknown wallets)
- Or tracked wallets bought during a brief WebSocket disconnect and were missed

If no tracked wallets were in the BC at all, the bot correctly had no signal — the 413 error didn't matter because there was nothing to find. But we can't confirm this without manually checking the BC transactions on-chain.

### Lessons

1. **The 413 bug needs fixing** — even if this specific case had no tracked traders, future VERY_FAST tokens with tracked traders WILL hit the same error and be silently dropped
2. **The pre-watch is the most reliable path** — it bypasses RPC entirely and catches tokens the migration-time scan would miss
3. **24 wallets may not be enough** — a $2.1M runner with zero tracked wallets suggests the registry needs expanding

---

## Related

- [[patterns/alert-outcomes-apr29]] — full session analysis
- [[patterns/alert-outcomes-apr27-28]] — Apr 27–28 analysis
- [[patterns/migration-speed-signal]] — speed tier definitions and data
- [[patterns/winner-checklist]] — go/no-go decision framework
