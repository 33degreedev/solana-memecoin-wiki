---
title: "Two-Day Alert System Review — May 5-6, 2026"
name: Two-Day Alert System Review — May 5-6, 2026
description: Combined analysis of May 5 and May 6 AFK scanner outcomes, focused on tier settings, skip policy, 10x+ main runners, trader attribution, and filters to test next.
type: analysis
status: draft
tags: [alert-quality, migration-speed, trader-analysis, skip-rules, main-runners, pnl-simulation]
sources:
  - "/Users/grip.eth/Documents/Codex/2026-05-06/files-mentioned-by-the-user-alerts/alerts_24h_2026-05-05_2340_enriched.csv"
  - "/Users/grip.eth/Documents/Codex/2026-05-06/files-mentioned-by-the-user-alerts/alerts_24h_2026-05-06_2240_enriched.csv"
---

# Two-Day Alert System Review — May 5-6, 2026

Summary: Across the May 5 and May 6 enriched alert batches, there were 108 rows, 42 tokens reached 2x+, 12 reached 5x+, and only 3 reached 10x+. The main-runner edge was not evenly distributed. It clustered around strong narratives, specific traders, and the non-STALLED speed tiers.

**Combined sample:** 108 rows  
**2x+ winners:** 42 / 108 = 38.9%  
**5x+ runners:** 12 / 108 = 11.1%  
**10x+ main runners:** 3 / 108 = 2.8%  
**Main-runner definition for this report:** 10x+ from alert market cap  
**Secondary runner definition:** 5x+  

---

## Executive Read

The strongest setting change is simple: **do not turn EXTREME off globally**. May 6 proved why: the skipped EXTREME bucket had the only 10x+ of that day and two 5x+ runners out of only three skipped EXTREME rows.

The second strongest rule is also simple: **keep STALLED off by default for main-runner hunting**. Across the two-day sample, STALLED had 13 rows, only 3 reached 2x, and none reached 5x or 10x. STALLED can occasionally produce a small trade, but it did not produce the main runners.

The third rule is the most important filter: **strong narrative is the best early runner clue in this dataset**. Strong narratives were only 17 rows, but produced all 3 of the 10x+ plays and 9 of the 12 total 5x+ runners.

---

## Combined Outcome by Tier

| Tier | Rows | 2x+ | 2x Rate | 5x+ | 5x Rate | 10x+ | Median Multiple | Max Multiple | Suggested Setting |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---|
| EXTREME | 33 | 15 | 45.5% | 3 | 9.1% | 1 | 1.90x | 20.83x | ON |
| FAST | 15 | 5 | 33.3% | 4 | 26.7% | 1 | 1.59x | 16.87x | ON |
| MODERATE | 18 | 7 | 38.9% | 3 | 16.7% | 1 | 1.58x | 24.15x | ON |
| MID | 16 | 6 | 37.5% | 2 | 12.5% | 0 | 1.76x | 8.61x | ON |
| SLOW | 8 | 4 | 50.0% | 0 | 0.0% | 0 | 2.13x | 4.66x | SOFT ON / WATCH |
| VERY_FAST | 5 | 2 | 40.0% | 0 | 0.0% | 0 | 1.72x | 2.50x | SOFT ON / WATCH |
| STALLED | 13 | 3 | 23.1% | 0 | 0.0% | 0 | 1.61x | 3.30x | OFF |

### Tier Decision

| Tier | Decision | Reason |
|---|---|---|
| EXTREME | ON | It caught one 10x+ and three 5x+ across both days. Turning it off caused the biggest miss on May 6. |
| FAST | ON | Highest 5x density in the combined sample: 4 of 15 rows reached 5x+. |
| MODERATE | ON | Produced the biggest two-day runner, SELLOR at 24.15x. |
| MID | ON | No 10x yet, but May 6 had two 5x+ MID runners. Do not cut it. |
| SLOW | Soft ON / watch-only | Useful for 2x scalps, but no 5x+ across both days. Consider lower priority or smaller size. |
| VERY_FAST | Soft ON / watch-only | Small sample, no main runners yet. Not enough evidence to kill it. |
| STALLED | OFF by default | Zero 5x+ and zero 10x+. Keep only rare manual overrides. |

---

## The 10x+ Main Runners

| Day | Token | Status | Tier | Traders | Trader Names | Daypart | Narrative Strength | Current MC/FDV | Post-Alert ATH MC | Max Multiple |
|---|---|---|---|---:|---|---|---|---:|---:|---:|
| May 5 | SELLOR / Michul Sellor | ALERTED | MODERATE | 2 | trenchman, cupsery | Afternoon | Strong | 495K | 858K | 24.15x |
| May 6 | soothsayer / The Man from the Future | SKIPPED | EXTREME | 3 | boomer, dv, theo | Evening | Strong | 219K | 734K | 20.83x |
| May 5 | wrdog / World Record Dog | ALERTED | FAST | 1 | chester | Overnight | Strong | 89K | 538K | 16.87x |

Pattern: all 3 main runners had **strong narrative**, but they did not share one trader-count bucket, one time of day, or one speed tier. This means strong narrative should be an override signal, while trader count and speed tier should rank the alert rather than hard-gate it.

---

## Trader Tally — 10x+ Attribution

Each trader gets one credit for every 10x+ row they appeared on.

| Trader | 10x+ Credits | 10x+ Token(s) |
|---|---:|---|
| boomer | 1 | soothsayer |
| chester | 1 | wrdog |
| cupsery | 1 | SELLOR |
| dv | 1 | soothsayer |
| theo | 1 | soothsayer |
| trenchman | 1 | SELLOR |

No trader appeared on more than one 10x+ play in this two-day sample. The important read is not "follow only one trader." The read is: when one of these traders appears on a strong narrative in an enabled tier, the alert deserves priority.

---

## Trader Tally — 5x+ Runner Attribution

| Trader | 5x+ Credits | 10x+ Credits | 5x+ Token(s) |
|---|---:|---:|---|
| cupsery | 3 | 1 | SELLOR, Nigga, Ryder |
| parsiix | 3 | 0 | Alzheimers, E, COMPUTA |
| boomer | 2 | 1 | soothsayer, COMPUTA |
| dv | 2 | 1 | AI, soothsayer |
| theo | 2 | 1 | soothsayer, E |
| trenchman | 2 | 1 | SELLOR, E |
| bandit | 2 | 0 | AI, PUMP |
| casino | 2 | 0 | AI, AI |
| chester | 1 | 1 | wrdog |
| clukzsol | 1 | 0 | FAG |
| decu | 1 | 0 | Alzheimers |
| errol | 1 | 0 | E |

Trader read:

- **cupsery** is the best two-day runner catcher by count: 3 separate 5x+ credits and 1 10x+ credit.
- **parsiix** did not hit a 10x+ in this sample, but appeared on 3 separate 5x+ plays. This is a high-quality runner signal.
- **theo, dv, boomer, trenchman, chester** all touched 10x+ outcomes and should be treated as priority confirmation traders.
- **bandit and casino** had multiple 5x+ credits, but no 10x+ here. Keep them on the runner list, but pair with narrative strength.
- **clukzsol** caught FAG, a 9.24x skipped EXTREME. That is below the 10x threshold, but important because it came from a disabled tier.

---

## Trader-Count Signal

| Trader Count | Rows | 2x+ | 2x Rate | 5x+ | 10x+ | Median Multiple | Max Multiple |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 13 | 3 | 23.1% | 0 | 0 | 1.61x | 3.30x |
| 1 | 55 | 25 | 45.5% | 6 | 1 | 1.84x | 16.87x |
| 2 | 24 | 10 | 41.7% | 3 | 1 | 1.77x | 24.15x |
| 3 | 11 | 2 | 18.2% | 2 | 1 | 1.41x | 20.83x |
| 4 | 5 | 2 | 40.0% | 1 | 0 | 1.29x | 8.61x |

Trader count alone is not a clean hard filter. The best 10x+ plays came from 1-trader, 2-trader, and 3-trader rows. More traders did not automatically mean better quality, but **1-2 traders was the best default bucket for consistency**.

Use 3+ traders as a context signal, not an auto-buy. The soothsayer 3-trader row worked because it also had a strong narrative and EXTREME speed. Without narrative, 3+ trader rows were noisy.

---

## Narrative Filter

| Narrative Strength | Rows | 2x+ | 2x Rate | 5x+ | 10x+ | Median Multiple | Max Multiple |
|---|---:|---:|---:|---:|---:|---:|---:|
| Strong | 17 | 11 | 64.7% | 9 | 3 | 6.24x | 24.15x |
| Weak | 40 | 16 | 40.0% | 3 | 0 | 1.77x | 9.24x |
| Medium | 51 | 15 | 29.4% | 0 | 0 | 1.61x | 4.51x |

This is the biggest filter discovery from the combined two-day study. **Strong narrative was the only bucket that produced 10x+ runners**, and it produced 75% of the 5x+ runners.

Medium narrative was the danger zone. It had the largest sample, but zero 5x+ and zero 10x+. Medium can still trade to 2x, but it should not receive main-runner sizing without another signal.

---

## Daypart Check

| Daypart | Rows | 2x+ | 2x Rate | 5x+ | 10x+ | Median Multiple | Max Multiple |
|---|---:|---:|---:|---:|---:|---:|---:|
| Afternoon | 34 | 13 | 38.2% | 4 | 1 | 1.54x | 24.15x |
| Evening | 39 | 15 | 38.5% | 5 | 1 | 1.72x | 20.83x |
| Morning | 23 | 10 | 43.5% | 2 | 0 | 1.90x | 6.69x |
| Overnight | 12 | 4 | 33.3% | 1 | 1 | 1.71x | 16.87x |

Time of day is not a hard filter. The 10x+ plays appeared overnight, afternoon, and evening. Afternoon/evening produced the most 5x+ runners by count, while morning had the best 2x hit rate. Use daypart for sizing and attention, not for on/off logic.

---

## Suggested Bot Settings

### Tiers

| Tier | Setting | Alert Type |
|---|---|---|
| EXTREME | ON | Full alert |
| FAST | ON | Full alert |
| MODERATE | ON | Full alert |
| MID | ON | Full alert |
| SLOW | ON but lower priority | Watch / smaller size / scalp bias |
| VERY_FAST | ON but lower priority | Watch until more data |
| STALLED | OFF by default | Manual override only |

### Override Rules

Turn a lower-priority or skipped token into a watchlist/entry candidate when at least two of these are true:

1. Strong narrative.
2. Trader is cupsery, parsiix, theo, dv, boomer, trenchman, chester, bandit, casino, or another proven runner wallet.
3. Tier is EXTREME, FAST, MODERATE, or MID.
4. Early post-migration candles show continuation instead of instant fade.
5. Current MC holds above alert MC after the first pullback.
6. Multiple runner traders appear within a tight window, but do not require this as a hard rule.

### Filters to Test Next

| Filter | Why It Matters |
|---|---|
| Strong narrative override | Caught all 3 10x+ plays and 9 of 12 5x+ plays. |
| Medium narrative penalty | Medium had 51 rows and zero 5x+. This bucket likely needs extra confirmation. |
| EXTREME re-enable | May 6 skipped EXTREME contained the only 10x+ of the day. |
| STALLED hard skip | STALLED had zero 5x+ across both days. |
| Runner-trader list | cupsery, parsiix, boomer, dv, theo, trenchman, chester, bandit, casino showed repeated runner involvement. |
| 1-2 trader default priority | Best consistency without eliminating all main runners. |
| 3+ trader narrative check | 3+ traders worked on soothsayer, but the bucket overall was weak without strong narrative. |
| Daypart weighting | Afternoon/evening produced more 5x+ by count, but not enough to hard filter. |

---

## Operating Strategy

Do not build the strategy around "buy every alert and sell 2x." The two-day data shows that the real edge is finding the few runners and letting them breathe. The better operating model is:

1. Alert full: EXTREME, FAST, MODERATE, MID.
2. Alert soft: SLOW and VERY_FAST.
3. Skip: STALLED, unless strong narrative plus proven trader plus continuation.
4. Size up only when narrative is strong or a proven runner trader is involved.
5. Take initials around 3x instead of selling everything close to 2x.
6. Leave runner allocation for 5x and 10x attempts.
7. Treat medium-narrative alerts as scalp trades unless a second signal confirms them.

The cleanest next experiment is **Core tiers ON + strong narrative/proven trader boost + STALLED off**. That keeps all observed 10x+ plays available while cutting the lowest-quality tier.

---

## Final Lesson

The bot should not be tuned only to improve raw 2x hit rate. A higher hit rate can still miss the only trade that pays for the whole batch. The goal is to avoid dead zones while preserving access to the rare asymmetric runners.

Across May 5 and May 6, the dead zone was STALLED. The asymmetric zone was strong narrative inside enabled tiers, especially when paired with a known runner trader. EXTREME must stay on, because turning it off is exactly how the May 6 soothsayer 20.83x was missed.

---

## Change Log

- 2026-05-07: Created combined two-day report from the May 5 and May 6 enriched alert CSVs and prior wiki pages.
