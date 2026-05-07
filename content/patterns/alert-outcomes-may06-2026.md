---
title: "Alert Outcome Analysis — May 6, 2026"
name: Alert Outcome Analysis — May 6, 2026
description: Post-mortem on 45 AFK scanner rows, including alerted and skipped tokens. Tests whether skipped tiers filtered losers without removing main runners, using post-alert ATH, current MC/FDV, 2x hit rate, narrative strength, and 0.05 SOL simulations.
type: analysis
status: draft
tags: [alert-quality, skipped-alerts, win-rate, migration-speed, narrative-strength, outcome-tracking, pnl-simulation]
source: "/Users/grip.eth/Documents/Codex/2026-05-06/files-mentioned-by-the-user-alerts/alerts_24h_2026-05-06_2240_enriched.csv"
---

# Alert Outcome Analysis — May 6, 2026

Summary: This batch tested 45 AFK scanner rows from the May 6 list, including both tokens that alerted and tokens that were skipped. The core question was whether the skip rules filtered losers without eliminating the main runners.

**Period:** May 6, 2026 PT  
**Total rows:** 45  
**Alerted rows:** 29  
**Skipped rows:** 16  
**Winner definition:** post-alert ATH reached at least 2x the alert market cap  
**Entry assumption for simulations:** 0.05 SOL per row  
**Sources:** enriched alert CSV generated from DexScreener current MC/FDV and GeckoTerminal minute OHLCV  

---

## Core Results

| Group | Rows | 2x+ Winners | 2x Hit Rate | Losers | Loser Rate | 5x+ Runners | 10x+ Runners |
|---|---:|---:|---:|---:|---:|---:|---:|
| All rows | 45 | 19 | 42.2% | 26 | 57.8% | 7 | 1 |
| Alerted | 29 | 14 | 48.3% | 15 | 51.7% | 5 | 0 |
| Skipped | 16 | 5 | 31.3% | 11 | 68.8% | 2 | 1 |
| Skipped STALLED | 13 | 3 | 23.1% | 10 | 76.9% | 0 | 0 |
| Skipped EXTREME | 3 | 2 | 66.7% | 1 | 33.3% | 2 | 1 |

The skip logic was directionally right on STALLED tokens: 10 of 13 skipped STALLED rows were losers, and none reached 5x. But the EXTREME skip rule failed badly in this sample. The 3 skipped EXTREME rows contained 2 main runners, including the only 10x+ outcome in the full batch.

---

## Results by Status and Tier

| Status | Tier | Rows | 2x+ Winners | 2x Hit Rate | Losers | Loser Rate | 5x+ Runners | 10x+ Runners |
|---|---|---:|---:|---:|---:|---:|---:|---:|
| ALERTED | EXTREME | 8 | 6 | 75.0% | 2 | 25.0% | 1 | 0 |
| ALERTED | FAST | 4 | 1 | 25.0% | 3 | 75.0% | 1 | 0 |
| ALERTED | MID | 7 | 3 | 42.9% | 4 | 57.1% | 2 | 0 |
| ALERTED | MODERATE | 6 | 2 | 33.3% | 4 | 66.7% | 1 | 0 |
| ALERTED | SLOW | 2 | 1 | 50.0% | 1 | 50.0% | 0 | 0 |
| ALERTED | VERY_FAST | 2 | 1 | 50.0% | 1 | 50.0% | 0 | 0 |
| SKIPPED | EXTREME | 3 | 2 | 66.7% | 1 | 33.3% | 2 | 1 |
| SKIPPED | STALLED | 13 | 3 | 23.1% | 10 | 76.9% | 0 | 0 |

### Tier Takeaways

- STALLED remains a good main-runner filter in this batch: it missed some 2x trades, but no 5x or 10x runners.
- EXTREME should not be globally turned off. Both alerted EXTREME and skipped EXTREME had high hit rates.
- FAST and MODERATE were weaker here than in the May 5 batch. This means the speed rule should be tested across days, not treated as fixed truth from one session.
- MID produced 2 of the 5 alerted 5x+ runners, so MID cannot be discarded.

---

## Missed Skipped Winners

| Token | Status | Tier | Skip Reason | Narrative Strength | Current MC/FDV | Post-Alert ATH MC | Max Multiple | Note |
|---|---|---|---|---|---:|---:|---:|---|
| soothsayer / The Man from the Future | SKIPPED | EXTREME | tier EXTREME off | Strong | 219K | 734K | 20.83x | Biggest missed runner and only 10x+ in the batch |
| FAG / Fake and Gay | SKIPPED | EXTREME | tier EXTREME off | Weak | 3K | 139K | 9.24x | Shock/internet phrase runner, dumped hard by current mark |
| mask / ratwifmask | SKIPPED | STALLED | tier STALLED skipped | Medium | 100K | 118K | 3.30x | Tradable 2x, but not a main runner |
| chort / chort | SKIPPED | STALLED | tier STALLED skipped | Weak | 22K | 74K | 2.30x | Small stalled winner |
| LUNADD / LUNA DD | SKIPPED | STALLED | tier STALLED skipped | Medium | 60K | 78K | 2.15x | Small stalled winner |

The important distinction: STALLED skipped winners were mostly small 2x-style trades. EXTREME skipped winners were actual runner material.

---

## Top Alerted Runners

| Token | Tier | Traders | Narrative Strength | Current MC/FDV | Post-Alert ATH MC | Max Multiple |
|---|---|---:|---|---:|---:|---:|
| E / Elon | MID | 4 | Strong | 18K | 299K | 8.61x |
| Ryder / The Chosen Inu | EXTREME | 1 | Strong | 3K | 434K | 6.98x |
| COMPUTA / You've Been Programmed | MODERATE | 2 | Strong | 80K | 228K | 6.78x |
| Nigga / Nigga | FAST | 1 | Weak | 104K | 132K | 6.29x |
| PUMP / PepeFart4BrettAsteroidInu | MID | 1 | Weak | 190K | 190K | 5.59x |
| FS / Full Send | EXTREME | 1 | Medium | 36K | 277K | 4.51x |
| LOBBYOOR / LOBBYOOR | MID | 1 | Medium | 58K | 146K | 4.07x |
| SCHIZO / SCHIZO | EXTREME | 1 | Weak | 29K | 169K | 4.04x |
| CODEBASE / CODEBASE | EXTREME | 1 | Medium | 47K | 108K | 3.88x |
| TAX / TAX | EXTREME | 1 | Medium | 14K | 41K | 3.71x |

---

## Narrative Strength

| Narrative Strength | Rows | 2x+ Winners | 2x Hit Rate | Losers | Loser Rate | 5x+ Runners | 10x+ Runners |
|---|---:|---:|---:|---:|---:|---:|---:|
| Strong | 7 | 4 | 57.1% | 3 | 42.9% | 4 | 1 |
| Medium | 26 | 8 | 30.8% | 18 | 69.2% | 0 | 0 |
| Weak | 12 | 7 | 58.3% | 5 | 41.7% | 3 | 0 |

Strong narrative was the best runner filter: 4 of 7 strong narratives reached 5x+, and the only 10x+ was strong. Medium narratives were noisy and did not produce main runners in this batch.

Weak narrative had a surprisingly high 2x hit rate because several raw meme or shock-phrase names moved, but that bucket needs tighter risk control. It can hit, but it is harder to underwrite.

---

## Portfolio Simulation — 0.05 SOL Per Row

| Group | Rows | Cost | 2x+ Hits | 5x+ Hits | 10x+ Hits | Sell ATH PnL | Hold Current PnL | Full 2.5x PnL | 3x/5x/10x Ladder PnL |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| All rows | 45 | 2.25 SOL | 19 | 7 | 1 | +4.845 SOL | -0.449 SOL | +0.220 SOL | +0.032 SOL |
| Alerted | 29 | 1.45 SOL | 14 | 5 | 0 | +2.970 SOL | -0.494 SOL | +0.260 SOL | -0.103 SOL |
| Skipped | 16 | 0.80 SOL | 5 | 2 | 1 | +1.875 SOL | +0.045 SOL | -0.040 SOL | +0.135 SOL |
| Skipped STALLED | 13 | 0.65 SOL | 3 | 0 | 0 | +0.472 SOL | -0.127 SOL | -0.143 SOL | -0.125 SOL |
| Skipped EXTREME | 3 | 0.15 SOL | 2 | 2 | 1 | +1.403 SOL | +0.172 SOL | +0.103 SOL | +0.260 SOL |
| Would Alert + Skipped EXTREME | 32 | 1.60 SOL | 16 | 7 | 1 | +4.373 SOL | -0.322 SOL | +0.363 SOL | +0.157 SOL |
| Would Alert + STALLED | 42 | 2.10 SOL | 17 | 5 | 0 | +3.442 SOL | -0.621 SOL | +0.117 SOL | -0.228 SOL |

Simulation assumptions:

- Every row receives a 0.05 SOL entry.
- "Sell ATH" assumes perfect exit at post-alert ATH.
- "Hold Current" marks all positions at current MC/FDV from the enriched CSV.
- "Full 2.5x" sells the full position at 2.5x when hit, otherwise marks at current.
- "3x/5x/10x Ladder" models partials into higher targets and marks unsold remainder at current.

The best practical adjustment in this batch was not to buy every skipped token. It was to add skipped EXTREME back into the alertable universe while keeping STALLED mostly filtered.

---

## Skip Rule Evaluation

| Rule | Verdict | Reason |
|---|---|---|
| Keep STALLED skipped | Yes, for main-runner hunting | 13 skipped STALLED rows had 0 5x+ and 0 10x+ runners. They were mostly loser-heavy with a few small 2x trades. |
| Turn EXTREME off globally | No | 3 skipped EXTREME rows included 2 5x+ runners and the only 10x+ runner. |
| Alert all EXTREME | Test with narrative/context filter | Alerted EXTREME was also strong: 6 winners out of 8, with 1 5x+ runner. |
| Require 2+ traders | No, not as a hard rule | Many runners had only 1 trader. Use trader count as confirmation, not a gate. |
| Use strong narrative as override | Yes | Strong narrative produced 4 of 7 5x+ runners and caught the missed soothsayer trade. |

---

## Working Strategy

The May 6 data says the bot should not skip EXTREME by default. EXTREME is too dangerous to turn off because it can contain the fastest consensus breakouts. The cleaner rule is:

1. Keep STALLED skipped by default for main-runner hunting.
2. Allow skipped EXTREME back in when narrative is strong, trader is credible, or early post-migration volume confirms.
3. Keep MID eligible because it produced multiple alerted 5x+ runners.
4. Do not require 2+ traders as a hard entry rule.
5. Use 2x as the win-rate benchmark, but do not build the whole TP plan around selling everything at 2x.

Preferred execution model:

| Rule | Setting |
|---|---|
| Main filter | Alerted rows plus skipped EXTREME overrides |
| Default skip | STALLED stays off unless there is an unusual catalyst |
| First take-profit | Initials around 3x, not close to 2x |
| Runner ladder | Leave size for 5x and 10x attempts |
| Bag policy | Do not hold dead trades just because ATH simulation looks profitable |
| Override trigger | Strong narrative, known trader, or explosive post-migration continuation |

---

## Synopsis Lesson

The May 6 lesson is very sharp: STALLED skipping worked for filtering main-runner losers, but EXTREME skipping cut out the best trade in the batch. If the goal is to avoid losers without missing the main runners, STALLED can stay filtered, but EXTREME needs a smarter override instead of a hard off switch.

The best next rule to test is **Alerted + skipped EXTREME override**, with STALLED still skipped by default. That simulated group had 32 entries, 16 2x+ winners, all 7 5x+ runners, and the only 10x+ runner. It beat the current alerted-only set on full 2.5x TP simulation and recovered the missed soothsayer runner.

Final lesson: the skip system should separate "slow likely loser" from "fast disabled but potentially explosive." STALLED is mostly a loser filter. EXTREME is a runner risk filter and should not be treated the same way.

---

## Change Log

- 2026-05-07: Created May 6 alert outcome page from the enriched May 6 CSV, including alerted-vs-skipped hit rates, skipped-tier evaluation, narrative strength, and TP simulations.
