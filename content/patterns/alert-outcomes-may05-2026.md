---
title: "Alert Outcome Analysis — May 5, 2026"
name: Alert Outcome Analysis — May 5, 2026
description: Post-mortem on 63 post-migration alerts called around 34K market cap. Tracks post-alert ATH, current MC/FDV, 2x win rate, migration-speed tier, trader-count signal, and 0.05 SOL simulations.
type: analysis
status: draft
tags: [alert-quality, win-rate, migration-speed, trader-count, outcome-tracking, pnl-simulation]
source: "/Users/grip.eth/Documents/Codex/2026-05-06/files-mentioned-by-the-user-alerts/alerts_24h_2026-05-05_2340_enriched.csv"
---

# Alert Outcome Analysis — May 5, 2026

Summary: This batch tested 63 post-migration alerts that were generally called around the 34K market-cap zone. The main question was whether these alerts ever offered a profitable post-alert exit window, which trader-count buckets performed best, and whether migration-speed tier helped separate runners from weak alerts.

**Period:** May 5, 2026 PT  
**Total alerts:** 63  
**Winner definition:** post-alert ATH reached at least 2x the alert market cap  
**Entry assumption for simulations:** 0.05 SOL per alert  
**Sources:** enriched alert CSV generated from DexScreener current MC/FDV and GeckoTerminal minute OHLCV  
**Confidence:** 61 high-confidence rows, 2 medium-confidence rows

---

## Core Results

| Threshold | Alerts Hit | Rate |
|---|---:|---:|
| 1.5x+ post-alert | 37 / 63 | 58.7% |
| 2x+ post-alert | 23 / 63 | 36.5% |
| 5x+ post-alert | 5 / 63 | 7.9% |
| 10x+ post-alert | 2 / 63 | 3.2% |

The batch had a decent number of tradable 2x opportunities, but true runners were rare. Only 5 alerts reached 5x+, and only 2 reached 10x+.

---

## Top Post-Alert Runners

| Rank | Token | Tier | Traders | Trader Names | Alert Time PT | Current MC/FDV | Post-Alert ATH MC | Max Multiple | ATH Time PT |
|---:|---|---|---:|---|---|---:|---:|---:|---|
| 1 | SELLOR / Michul Sellor | MODERATE | 2 | trenchman, cupsery | 2026-05-05 03:22 PM | 495K | 858K | 24.15x | 2026-05-05 06:02 PM |
| 2 | wrdog / World Record Dog | FAST | 1 | chester | 2026-05-05 02:53 AM | 89K | 538K | 16.87x | 2026-05-05 05:30 AM |
| 3 | Alzheimers / Buy & Forget | MODERATE | 2 | decu, parsiix | 2026-05-05 07:50 PM | 176K | 286K | 8.62x | 2026-05-05 10:27 PM |
| 4 | AI / Artificial Inu | FAST | 1 | casino | 2026-05-05 11:50 AM | 74K | 211K | 6.69x | 2026-05-05 06:54 PM |
| 5 | AI / Artificial Inu | FAST | 3 | dv, bandit, casino | 2026-05-05 11:50 AM | 14K | 216K | 6.24x | 2026-05-05 02:30 PM |
| 6 | 1 / 1 min a day | SLOW | 1 | cupsery | 2026-05-05 09:40 AM | 3K | 137K | 4.66x | 2026-05-05 09:47 AM |
| 7 | turdcoin / turdcoin | EXTREME | 1 | nyhrox | 2026-05-05 05:58 AM | 24K | 141K | 4.34x | 2026-05-05 06:01 AM |
| 8 | LUKE / Luke Battles Cancer Fund | SLOW | 1 | parsiix | 2026-05-05 10:06 AM | 4K | 142K | 4.26x | 2026-05-05 12:02 PM |
| 9 | LOBBYOOR / Bitcoin Policy Institute | MID | 1 | cupsery | 2026-05-05 11:02 PM | 58K | 146K | 4.07x | 2026-05-05 11:16 PM |
| 10 | Roho / Roho | MODERATE | 1 | nyhrox | 2026-05-05 08:19 AM | 6K | 91K | 3.31x | 2026-05-05 08:41 AM |

---

## Results by Migration-Speed Tier

| Tier | Speed Bucket | Alerts | 2x+ Winners | 2x Win Rate | 5x+ Runners | Median Max Multiple |
|---|---|---:|---:|---:|---:|---:|
| EXTREME | 0-1.5m | 22 | 7 | 31.8% | 0 | 1.72x |
| VERY_FAST | 1.5-3m | 3 | 1 | 33.3% | 0 | 1.37x |
| FAST | 3-5m | 11 | 4 | 36.4% | 3 | 1.59x |
| MODERATE | 5-10m | 12 | 5 | 41.7% | 2 | 1.35x |
| MID | 10-15m | 9 | 3 | 33.3% | 0 | 1.71x |
| SLOW | 15-20m | 6 | 3 | 50.0% | 0 | 2.13x |

### Tier Takeaways

- FAST and MODERATE produced every 5x+ runner in this batch.
- SLOW had the highest 2x win rate, but no 5x+ runners.
- EXTREME had the most alerts and many small wins, but none reached 5x+.
- MID produced some tradable moves, but no main runners.

Interpretation: fastest migration was not automatically best. The strongest runners clustered in the middle speed bands, especially FAST and MODERATE.

---

## Results by Trader Count

| Traders | Alerts | 2x+ Winners | Win Rate | Sold ATH PnL | Sell 2x PnL | Still Holding PnL |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 36 | 14 | 38.9% | +2.901 SOL | -0.289 SOL | -1.080 SOL |
| 2 | 15 | 7 | 46.7% | +2.130 SOL | -0.012 SOL | +0.275 SOL |
| 3 | 9 | 1 | 11.1% | +0.406 SOL | -0.319 SOL | -0.399 SOL |
| 4 | 3 | 1 | 33.3% | +0.088 SOL | -0.032 SOL | -0.121 SOL |

Simulation assumptions:

- Every alert receives a 0.05 SOL entry.
- "Sold ATH" assumes perfect exit at post-alert ATH.
- "Sell 2x" assumes a position is sold at exactly 2x if it reaches 2x; otherwise it is marked at current value.
- "Still Holding" marks every alert at current value from the enriched CSV.

### Trader-Count Takeaways

- 2-trader alerts had the best 2x win rate at 46.7%.
- 1-trader alerts still produced 14 winners and 2 of the 5 main runners.
- 3-trader alerts underperformed badly in this batch: 1 winner out of 9.
- More traders did not automatically mean better alert quality.

Important refinement: 2+ traders is a useful signal, but it is not mandatory for runners. The largest two outcomes were split: SELLOR had 2 traders, while wrdog had only 1 trader.

---

## Portfolio Simulation — 0.05 SOL Per Alert

| Strategy | Final Value | PnL |
|---|---:|---:|
| Spend 0.05 SOL on all 63 alerts | 3.150 SOL cost | — |
| Sell every alert at post-alert ATH | 8.674 SOL | +5.524 SOL |
| Sell at 2x when reached, otherwise hold current | 2.498 SOL | -0.652 SOL |
| Still holding all positions | 1.825 SOL | -1.325 SOL |

The perfect-ATH strategy was strongly profitable, but this is not executable in practice. The mechanical 2x strategy lost money because the losers and current marks outweighed the capped winners. Still holding the full batch was worse.

Key implication: this alert stream can identify tokens that eventually move, but exit quality matters heavily. Capturing runners requires either a trailing strategy or a better rule for filtering losers before entry.

---

## Results by Time of Day

| Daypart | Alerts | 2x+ Winners | 5x+ Runners | Median Max Multiple |
|---|---:|---:|---:|---:|
| Overnight | 10 | 3 | 1 | 1.56x |
| Morning | 22 | 10 | 2 | 1.93x |
| Afternoon | 20 | 5 | 1 | 1.39x |
| Evening | 11 | 5 | 1 | 1.82x |

Morning had the highest count of 2x+ winners and the best median multiple. However, 5x+ runners appeared across multiple dayparts, so time of day is a secondary filter, not a standalone rule.

---

## Pattern Notes

### Pattern 1 — FAST and MODERATE produced the main runners

All 5 alerts that reached 5x+ came from FAST or MODERATE tiers. This suggests the best runner zone in this batch was not the absolute fastest migration bucket. EXTREME generated many alerts and several 2x wins, but no 5x+ outcomes.

Rule candidate: prioritize FAST and MODERATE when looking for main runners, but do not fully discard SLOW because it had a high 2x hit rate.

### Pattern 2 — 2 traders was the best consensus bucket

2-trader alerts had the highest win rate at 46.7% and included 2 of the top 3 runners: SELLOR and Alzheimers. This supports the idea that light consensus can improve signal quality.

But 1-trader alerts still mattered. wrdog, AI, turdcoin, LUKE, LOBBYOOR, and Roho were all 1-trader alerts in the top 10.

Rule candidate: require 2+ traders only if the goal is consistency. Do not require 2+ traders if the goal is catching all main runners.

### Pattern 3 — 3+ traders did not confirm quality

3-trader alerts produced only 1 winner out of 9. The 3-trader AI row was a runner, but the bucket overall was weak. This contradicts a simple "more traders = better" thesis for this day.

Rule candidate: treat 3+ traders as a context signal, not an automatic entry. Pair it with tier, narrative quality, and trader identity.

### Pattern 4 — Holding was structurally weak

Still holding all 63 alerts would be down 1.325 SOL on a 3.15 SOL deployment. This is important because many alerts did become profitable at some point, but later gave back value.

Rule candidate: alerts are better treated as trade opportunities than long holds unless the token is showing unusual continuation strength.

### Pattern 5 — Mechanical 2x sells were not enough

Selling every 2x hit at exactly 2x still lost 0.652 SOL if all non-2x alerts were held to current value. This means the strategy needs either:

- tighter invalidation on losers,
- partial exits plus trailing winners,
- better entry filtering,
- or a rule that avoids buying every alert.

---

## Working Rules to Test Next

1. Prioritize FAST and MODERATE for runner hunting.
2. Keep 1-trader alerts eligible if the trader is high quality or the narrative is strong.
3. Treat 2-trader alerts as the strongest default consensus bucket in this sample.
4. Do not assume 3+ traders means higher quality.
5. Avoid "buy all and hold" behavior.
6. Test a rule that takes partial profit at 2x but lets a runner portion trail.
7. Separate "tradable 2x opportunity" from "main runner candidate" in future tagging.

---

## Change Log

- 2026-05-06: Created new standalone analysis page from the final enriched May 5 alert CSV. Existing wiki pages were not modified.
