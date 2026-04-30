---
name: Migration Signals — Pattern Library
type: pattern
tags: [pattern, signal]
---

# Migration Signals — Pattern Library

> **Data confidence: LOW** — Based on 1 confirmed migration (embers). All thresholds are hypotheses, not validated rules. Need 10–20 cases minimum.

What does a winning pump.fun → pumpAMM migration look like in the first 2 minutes of on-chain data?

---

## What Is Migration?

When a pump.fun bonding curve fills (~$69K in buys), the token **graduates** to pumpAMM. A new liquidity pool opens and trading resumes immediately. The first 2 minutes of pumpAMM trading reveal whether the token has legs or collapses.

**Why the first 2 minutes matter:** BC holders (who bought at lower prices) immediately dump into the new liquidity. How the market absorbs that dump determines if the token survives.

---

## The Standard Migration Pattern (Single Case — embers)

```
t=0s:   pumpAMM pool opens. First trade: tiny sniper ($4–5, 0.05 SOL).

t=5s:   IMMEDIATE large sell ($270).
        BC holder exits into fresh AMM liquidity.
        EXPECTED — they've been sitting for 23 min at lower prices.
        DO NOT PANIC SELL. This is normal.

t=8s:   Whale enters ($169, 1.98 SOL) and buys the dump.
        Smart money signal — recognizes BC sell as temporary.
        THIS IS THE KEY SIGNAL.

t=13–29s: Bot accumulates 8× micro-buys ($0.08 each).
          Programmatic conviction = bots pass their filter.

t=28s:  The t+8s whale flips (+29% in 20 seconds).
        Fastest trade in the dataset.

t=30–60s: FLIP. 11 buys vs 1 sell. +$257 net.
          Dump absorbed. Momentum confirmed.

t=45s:  Optimal entry window (in this case).
```

---

## BC Phase Signals (Pre-Migration)

These signals are visible BEFORE migration and predict migration quality.

| Signal | embers | Interpretation |
|--------|--------|----------------|
| BC fill time | 23 minutes | Moderate — real demand, not just dev pump |
| Dev buy at launch | $856 (10 SOL) | Conviction — not a rug setup |
| First 2s sniper wave | 16 wallets, $7,303 | Automated systems detected high-quality launch |
| Multi-buy wallets in first 2s | 5 | Bot conviction — passed automated filter |
| Buy/sell ratio (first 2s) | 23:2 | Extreme buy dominance |

### BC Fill Time Interpretation (Hypothesis)
| Fill Time | Assessment |
|-----------|-----------|
| < 10 min | 🟢 Very strong — intense demand |
| 10–25 min | 🟢 Strong — sustained real buying |
| 25–45 min | 🟡 Moderate — enough demand to graduate |
| > 45 min | 🔴 Slow — may lack post-migration momentum |

---

## Post-Migration Thresholds (t=0 to t=30s)

Check these at t=30s. Enter at t=45s if all pass.

| Signal | embers Value | Suggested Threshold | Pass? |
|--------|-------------|--------------------|----|
| Total volume (30s) | $752 | > $300 | ✅ |
| Largest single buy | $169 | > $100 | ✅ |
| Bot accumulation | 8 micro-buys (CYZcucbb) | Same wallet 3+ buys | ✅ |
| Buy tx count vs sell | 12 buys / 8 sells | Buys > Sells | ✅ |
| Net sell pressure | -$380 | < -$500 | ✅ |
| Jupiter routing live | Yes | Required | ✅ |

### Hard No-Entry Rules
- ❌ Zero buys > $50 in first 30s — no smart money
- ❌ Only 1–2 unique buy wallets — manipulation risk
- ❌ Net sell pressure > -$1,000 — coordinated dump, not BC exit

---

## Platforms to See at Migration

A healthy migration shows activity on multiple routing platforms immediately:

| Platform | Role | Signal |
|----------|------|--------|
| pAMMBay (pumpAMM) | The migrated pool | Required — confirms graduation |
| Flashtrade | Fast bots | ✅ Active = bots detected it |
| Jupiter | Aggregator routing | ✅ Indexed within 15s = broad market visibility |
| BBRouter / s7Sunwr | Multi-router | ✅ Multiple routers = breadth of market awareness |

---

## BC vs Post-Migration Volume Comparison (embers)

| Phase | Window | Volume | Buy % | Txs |
|-------|--------|--------|-------|-----|
| BC (first 2 seconds) | t=0 to t+1s | $7,351 | 99.3% | 25 |
| Post-migration | t=0 to t+30s | $752 | 24.8% | 20 |
| Post-migration | t=0 to t+120s | $2,407 | 54.1% | 75 |

**Key takeaway:** The BC launch is always 10× hotter than post-migration. The post-migration dump (24.8% buy in first 30s) is normal — this is BC holders cashing out. The question is whether buyers absorb the dump.

---

## How to Get the Data

**Pre-migration BC data:**
- Solscan: DeFi Activities export for the bonding curve account address
- GeckoTerminal: `api.geckoterminal.com/api/v2/networks/solana/pools/{BC_pool}/trades` (may only have first 25 trades)
- DexScreener: Token page shows BC pool address

**Post-migration pumpAMM data:**
- Solscan: DeFi Activities export for token address — filter to pumpAMM transactions after migration timestamp
- GeckoTerminal: Same endpoint for pumpAMM pool address

**Migration timestamp:** Visible in Solscan as the graduation transaction or as the first trade on the pumpAMM pool.

---

## Data Gaps for Future Collection

For each new migration studied, capture:
- [ ] BC fill time (launch tx timestamp → migration tx timestamp)
- [ ] Dev buy size and % of supply
- [ ] Number of unique BC buyers (Solscan holder count at migration)
- [ ] First 30s post-migration volume by bucket
- [ ] Largest single buy in first 30s
- [ ] Number of routing platforms active in first 60s
- [ ] Token price at migration vs price at t+5min, t+30min, t+60min (outcome)

---

## Related Pages

- [[coins/coin-index]]
- [[coins/embers]]
- [[patterns/volume-fingerprints]]
- [[patterns/winner-checklist]]
- [[playbooks/migration-alert]]
