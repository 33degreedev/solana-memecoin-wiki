---
title: "Alert Outcome Analysis — April 29, 2026"
name: Alert Outcome Analysis — April 29, 2026
description: Full post-mortem on 26 migration alerts fired by the VPS-deployed detector on Apr 29. Win rate by tier, trader leaderboard, pattern analysis, and P&L simulations.
type: analysis
status: complete
tags: [alert-quality, win-rate, patterns, system-improvement, outcome-tracking]
---

# Alert Outcome Analysis — April 29, 2026

**Period:** Apr 29, 2026 (00:59–09:11 UTC)
**Total alerts:** 26
**2x definition:** ATH market cap > $70K post-migration
**Data sources:** GeckoTerminal OHLCV, DexScreener, bot alert_cache.db (VPS)
**Bot status:** First full session on DigitalOcean VPS (deployed Apr 28)

---

## Results by Tier

| Tier | 2x | Total | Win Rate |
|---|---|---|---|
| EXTREME | 4 | 7 | 57% |
| VERY_FAST | 1 | 1 | 100% |
| FAST | 0 | 3 | 0% |
| MODERATE | 2 | 4 | 50% |
| SLOW | 2 | 6 | 33% |
| STALLED | 1 | 5 | 20% |
| **TOTAL** | **10** | **26** | **38%** |

### Winners (confirmed ATH > $70K)

| Tier | Name | Peak MC | Traders in BC | Total SOL |
|---|---|---|---|---|
| EXTREME | Actually Useless | $224K | 1 (parsiix) | 2.38 |
| SLOW | chadhouse | $110K | 2 (chester, dv) | 6.70 |
| EXTREME | Mr. Nice Guy | $102K | 1 (kevnszn) | 4.39 |
| MODERATE | sam moonman | $98K | 2 (dv, parsiix) | 3.93 |
| VERY_FAST | OpenAI Coin | $92K | 2 (dv, west) | 13.33 |
| EXTREME | Broke Retards On Solana | $86K | 3 (theo, chester, dv) | 8.95 |
| STALLED | Frok | $83K | 2 (theo, parsiix) | 5.49 |
| EXTREME | Garlic Dog | $76K | 4 (dv, chester, jijo, parsiix) | 9.01 |
| SLOW | TerminAItor | $73K | 1 (dv) | 3.45 |
| MODERATE | Ewun Mogman | $70K | 1 (trenchman) | 4.89 |

### Near-Misses (ATH $45–69K)

| Tier | Name | ATH MC | Gap to 2x | Traders |
|---|---|---|---|---|
| SLOW | The Human | $64K | -$6K | trenchman, errol, bandit |
| STALLED | Chudjak | $56K | -$14K | chester |
| FAST | Ketalon | $49K | -$21K | nosa1x, parsiix |

### Hard Failures (ATH ≤ $40K — never meaningfully left migration MC)

| # | Token | Tier | Est. ATH | Traders |
|---|-------|------|----------|---------|
| 1 | VAMPCOIN | EXTREME | $36K | jijo |
| 2 | codemaxxing | EXTREME | ~$35K | chester |
| 3 | Psyop ("You have to buy this") | FAST | ~$35K | decu, dv |
| 4 | AGI ("Abeyant Goblins Inside") | FAST | ~$35K | chester, dv |
| 5 | the farm | SLOW | ~$35K | trenchman, errol |
| 6 | GremlinCoin | STALLED | ~$35K | dv, trenchman |
| 7 | PumperNickel | MODERATE | ~$35K | dv |
| 8 | LIL FCKIN GOBLIN (LFG) | SLOW | $34K | dv, errol, trenchman |
| 9 | That Fucking Bird (LARRY) | SLOW | ~$35K | west |
| 10 | Agent Tusk | MODERATE | ~$35K | kevnszn, leck |
| 11 | Just-Dice | STALLED | ~$35K | errol |
| 12 | agent tusk (copy) | STALLED | ~$35K | kevnszn, errol |
| 13 | Goolag | EXTREME | ~$35K | nosa1x |

---

## Pattern Analysis

### Pattern 1 — EXTREME tier improved dramatically (57% vs 30% on Apr 27–28)

7 EXTREME alerts, 4 winners. This is a major shift from the previous session where EXTREME was 30% (3/10). The winners all had identifiable hooks: Actually Useless (viral self-deprecating meme), Mr. Nice Guy (Trump Truth Social post linked on DexScreener), BROS (degen community identity), Garlic Dog (4-trader consensus — highest trader count in dataset).

The 3 EXTREME losers: VAMPCOIN (vampire naming = negative signal), codemaxxing (generic), Goolag (derivative of Google).

**Key difference from Apr 27–28:** the EXTREME winners this session had more known-trader SOL committed. Garlic Dog had 9.01 SOL across 4 traders. BROS had 8.95 across 3. The losers had 1-2 SOL from single traders. **Total BC SOL is a better predictor than tier speed for EXTREME alerts.**

---

### Pattern 2 — VERY_FAST is a new tier that produced a winner

OpenAI Coin migrated with VERY_FAST speed and hit $92K. This is the first appearance of this tier in the dataset. Two traders (dv + west) committed 13.33 SOL total — the highest SOL commitment of any alert this session. The combination of extreme speed + high SOL + recognizable brand name (OpenAI) created a strong setup.

**Note:** west committed 9.88 SOL — the single largest position in the entire dataset. This trader was new to the tracker but showed immediate high-conviction behavior.

---

### Pattern 3 — Copy token pattern reconfirmed: Agent Tusk appeared twice

Agent Tusk (2zT8K..., MODERATE, alerted at 07:45) and agent tusk (3niS4..., STALLED, alerted at 09:11). Both failed. The first had kevnszn + leck. The copy had kevnszn + errol. Same pattern as Dog In Vest / Vesting in Apr 27–28. The original didn't even win — and the copy still attracted known traders (kevnszn appeared in both). **The duplicate name detector would have caught this.**

---

### Pattern 4 — dv appeared on 6 winners but also 5 losers

In the Apr 27–28 session, dv was described as "0 confirmed hard failures." That no longer holds. This session dv appeared on: Psyop ❌, AGI ❌, GremlinCoin ❌, PumperNickel ❌, LFG ❌. All hard failures.

However, dv's win rate is still 55% (6/11) — significantly above the session average of 38%. And critically, dv's winners include every tier: EXTREME (BROS, Garlic Dog), VERY_FAST (OpenAI), MODERATE (sam moonman), SLOW (chadhouse, TerminAItor). **dv remains the best signal but is not infallible. dv alone is insufficient — the narrative filter still matters.**

---

### Pattern 5 — parsiix is the most efficient trader (4/5 = 80% hit rate)

parsiix appeared on 5 alerts: Actually Useless ✅, Garlic Dog ✅, sam moonman ✅, Frok ✅, Ketalon (near-miss). That's 4 winners out of 5, an 80% hit rate. parsiix also had the session's biggest winner (Actually Useless, $224K).

Combined with the Apr 27–28 data where parsiix had 2 winners, the cumulative record is 6 winners across 2 sessions. **parsiix picks winners at a higher rate than any other tracked trader.**

---

### Pattern 6 — 3+ trader consensus produced the highest peaks again

| Token | Traders | Peak MC |
|---|---|---|
| BROS | 3 (theo, chester, dv) | $86K |
| Garlic Dog | 4 (dv, chester, jijo, parsiix) | $76K |

This matches the Apr 27–28 pattern where both 3-trader alerts hit $100K+. Garlic Dog had the highest trader count of any alert (4) and won. The Human also had 3 traders but was a near-miss ($64K) — 3 traders + weak narrative ≠ winner.

**Refinement:** 3+ traders is a positive signal, but narrative quality determines if it breaks $70K. The Human had 3 traders but no narrative hook. Garlic Dog had 4 traders AND a memeable name.

---

### Pattern 7 — High SOL commitment ≠ guaranteed win

LARRY had west committing 8.89 SOL (single largest individual bet) and still failed. Agent Tusk had kevnszn at 10.13 SOL — also failed. **Individual high SOL is not predictive by itself.** What matters is SOL from multiple traders (consensus) or SOL from the most accurate traders (dv, parsiix).

Compare: OpenAI Coin had 13.33 SOL from 2 traders (dv + west) and won $92K. But LARRY had 8.89 SOL from west alone and failed. **Multi-trader SOL > single-trader SOL.**

---

### Pattern 8 — STALLED win rate dropped (20% vs 40% on Apr 27–28)

Only 1 STALLED winner (Frok, $83K) out of 5 alerts. The Apr 27–28 session's STALLED thesis was "a trader accumulating for 30 minutes has conviction." This session's STALLED losers included GremlinCoin (dv + trenchman) and agent tusk #2 (kevnszn + errol) — multi-trader STALLED alerts that still failed. **STALLED is not inherently high-quality. The pre-watch conviction thesis holds only when the traders involved have high hit rates (parsiix, dv on good narratives).**

---

### Pattern 9 — New traders: west, errol, jijo, nosa1x, leck, bandit

6 traders appeared for the first time. Quick assessment:

| Trader | Alerts | Winners | Win Rate | Notes |
|---|---|---|---|---|
| west | 2 | 1 (OpenAI) | 50% | Huge SOL size (9.88 avg). Mixed — big win, big loss |
| errol | 5 | 0 | 0% | Appeared on 5 alerts, 0 winners. Noise trader |
| jijo | 2 | 1 (Garlic Dog) | 50% | Early data — need more |
| nosa1x | 2 | 0 | 0% | Goolag ❌, Ketalon near-miss |
| leck | 1 | 0 | 0% | Only appeared once (Agent Tusk) |
| bandit | 1 | 0 | 0% | Only appeared once (The Human near-miss) |

**errol is the session's noisiest trader** — 5 appearances, 0 winners. If errol is in BC without a higher-quality trader present, the alert is likely noise.

---

## Synopsis

The Apr 29 session produced a **38% win rate on 26 alerts**, slightly better than the Apr 27–28 session (32% on 31 alerts). The detector's first full session on the VPS ran without interruption and captured a higher-quality batch of alerts.

**Key shifts from the previous session:**

1. **EXTREME improved from 30% to 57%** — driven by higher SOL commitment and better narratives in winning tokens. EXTREME + high total SOL + identifiable narrative = real signal.

2. **dv is still the best signal but now has confirmed failures.** 6/11 win rate (55%) vs 5/10+ in the previous session. The difference: dv's failures this session all had weak/no narratives (Psyop, PumperNickel, GremlinCoin). **dv in BC + strong narrative = high conviction. dv in BC + no narrative = noise.**

3. **parsiix is the most accurate tracker** — 4/5 (80%) this session. Combined across both sessions: the trader to watch.

4. **Copy token pattern reconfirmed** — Agent Tusk appeared twice, both failed. Duplicate detector would have caught the second.

5. **New trader errol is a negative signal** — 0/5 wins. If errol is the only known trader in BC, consider skipping.

---

## P&L Simulation — 0.1 SOL per Alert, Sell at ATH

**Assumptions**
- Entry MC: $33K (pump.fun migration price)
- Exit: peak ATH market cap — theoretical sell at exact top
- Position: 0.1 SOL per trade, no fees or slippage
- Hard failures estimated at $33–36K ATH

**Total trades:** 26
**Total deployed:** 2.6 SOL

---

### Winners

| Token | Tier | Peak MC | Mult | Return | P&L |
|---|---|---|---|---|---|
| Actually Useless | EXTREME | $224K | 6.78x | 0.678 SOL | +0.578 SOL |
| chadhouse | SLOW | $110K | 3.33x | 0.333 SOL | +0.233 SOL |
| Mr. Nice Guy | EXTREME | $102K | 3.09x | 0.309 SOL | +0.209 SOL |
| sam moonman | MODERATE | $98K | 2.97x | 0.297 SOL | +0.197 SOL |
| OpenAI Coin | VERY_FAST | $92K | 2.78x | 0.278 SOL | +0.178 SOL |
| BROS | EXTREME | $86K | 2.61x | 0.261 SOL | +0.161 SOL |
| Frok | STALLED | $83K | 2.52x | 0.252 SOL | +0.152 SOL |
| Garlic Dog | EXTREME | $76K | 2.31x | 0.231 SOL | +0.131 SOL |
| TerminAItor | SLOW | $73K | 2.22x | 0.222 SOL | +0.122 SOL |
| Ewun Mogman | MODERATE | $70K | 2.13x | 0.213 SOL | +0.113 SOL |
| **Subtotal** | | | | **3.074 SOL** | **+2.074 SOL** |

### Near-Misses

| Token | Tier | Peak MC | Mult | Return | P&L |
|---|---|---|---|---|---|
| The Human | SLOW | $64K | 1.95x | 0.195 SOL | +0.095 SOL |
| Chudjak | STALLED | $56K | 1.70x | 0.170 SOL | +0.070 SOL |
| Ketalon | FAST | $49K | 1.49x | 0.149 SOL | +0.049 SOL |
| **Subtotal** | | | | **0.514 SOL** | **+0.214 SOL** |

### Hard Failures

| Token | Tier | Est. Peak | Mult | Return | P&L |
|---|---|---|---|---|---|
| VAMPCOIN | EXTREME | $36K | 1.09x | 0.109 SOL | +0.009 SOL |
| 11 tokens @ ~$35K | Various | $35K | 1.06x | 1.166 SOL | +0.066 SOL |
| LFG | SLOW | $34K | 1.03x | 0.103 SOL | +0.003 SOL |
| **Subtotal** | | | | **1.378 SOL** | **+0.078 SOL** |

---

### Full Summary

| Category | Trades | Deployed | Returned | P&L |
|---|---|---|---|---|
| Winners | 10 | 1.0 SOL | 3.074 SOL | **+2.074 SOL** |
| Near-Misses | 3 | 0.3 SOL | 0.514 SOL | **+0.214 SOL** |
| Hard Failures | 13 | 1.3 SOL | 1.378 SOL | **+0.078 SOL** |
| **TOTAL** | **26** | **2.6 SOL** | **4.966 SOL** | **+2.366 SOL** |

| | |
|---|---|
| Deployed | 2.6 SOL |
| Returned | 4.966 SOL |
| Net P&L | **+2.366 SOL** |
| ROI | **+91%** |

---

## P&L Simulation — 2x Take-Profit

**Rules:** Tokens hitting $66K MC → auto-sell at 2x. Tokens that never reach $66K → sell at ATH (same as base).

All 10 winners hit 2x → each returns 0.200 SOL → winners subtotal: 2.000 SOL
Near-misses unchanged: 0.514 SOL
Hard failures unchanged: 1.378 SOL

| | |
|---|---|
| Deployed | 2.6 SOL |
| Returned | 3.892 SOL |
| Net P&L | **+1.292 SOL** |
| ROI | **+50%** |

**Left on table:** 1.074 SOL from winners (Actually Useless alone lost 0.478 SOL of upside).

---

## P&L Simulation — Tiered Exit

**Rules:**
- TP1: sell 50% at 2x ($66K MC)
- TP2: sell 30% at 3x ($99K MC)
- TP3: sell remaining 20% at trailing stop −20% from peak
- No TP fires → trailing stop on full position at peak × 0.80

### Winners — Hits 3x+ (3 tokens)

| Token | Peak | TP1 (50%@2x) | TP2 (30%@3x) | TP3 (20%@peak×0.8) | Total | P&L |
|---|---|---|---|---|---|---|
| Actually Useless | 6.78x | 0.100 | 0.090 | 0.109 | **0.299** | +0.199 |
| chadhouse | 3.33x | 0.100 | 0.090 | 0.053 | **0.243** | +0.143 |
| Mr. Nice Guy | 3.09x | 0.100 | 0.090 | 0.049 | **0.239** | +0.139 |

### Winners — Hits 2x but not 3x (7 tokens)

| Token | Peak | TP1 (50%@2x) | Remaining 50% @trailing | Total | P&L |
|---|---|---|---|---|---|
| sam moonman | 2.97x | 0.100 | 0.119 | **0.219** | +0.119 |
| OpenAI Coin | 2.78x | 0.100 | 0.111 | **0.211** | +0.111 |
| BROS | 2.61x | 0.100 | 0.104 | **0.204** | +0.104 |
| Frok | 2.52x | 0.100 | 0.101 | **0.201** | +0.101 |
| Garlic Dog | 2.31x | 0.100 | 0.092 | **0.192** | +0.092 |
| TerminAItor | 2.22x | 0.100 | 0.089 | **0.189** | +0.089 |
| Ewun Mogman | 2.13x | 0.100 | 0.085 | **0.185** | +0.085 |

**Winners subtotal: 2.182 SOL returned on 1.0 SOL — P&L: +1.182 SOL**

### Near-Misses — Trailing stop on full position

| Token | Peak | Trailing Exit | Return | P&L |
|---|---|---|---|---|
| The Human | 1.95x | 1.56x | 0.156 | +0.056 |
| Chudjak | 1.70x | 1.36x | 0.136 | +0.036 |
| Ketalon | 1.49x | 1.19x | 0.119 | +0.019 |

**Near-misses subtotal: 0.411 SOL returned on 0.3 SOL — P&L: +0.111 SOL**

### Hard Failures — Trailing stop on full position

Most at 1.06x → trailing at 0.85x → 0.085 SOL each
11 × 0.085 = 0.935 | VAMPCOIN (1.09x) = 0.087 | LFG (1.03x) = 0.082

**Hard failures subtotal: 1.104 SOL returned on 1.3 SOL — P&L: −0.196 SOL**

---

### All Strategies Comparison

| Strategy | Deployed | Returned | P&L | ROI |
|---|---|---|---|---|
| ATH exit | 2.6 SOL | 4.966 SOL | +2.366 SOL | **+91%** |
| 2x take-profit | 2.6 SOL | 3.892 SOL | +1.292 SOL | **+50%** |
| Tiered exit | 2.6 SOL | 3.697 SOL | +1.097 SOL | **+42%** |

---

### What the Apr 29 Math Tells Us

**2x TP outperforms tiered this session (+50% vs +42%).** This is the opposite of the Apr 27–28 result. The reason: no massive outlier. The biggest winner was Actually Useless at 6.78x — meaningful but not extreme. In the previous session, Vesting (9.3x) and Justice For Luca (6.97x) made the trailing slice on tiered worthwhile. Here, only 3 tokens hit 3x+, and the trailing slice on a 6.78x is only 0.109 SOL.

**The tiered strategy's value proposition is outlier capture.** When the session contains no 10x+ runners, the trailing slice adds complexity without proportional reward. The 2x TP is simpler and more profitable in a "normal" session.

**However, you don't know in advance which session has the outlier.** The Apr 27–28 session had SCAM (485x) and Vesting (9.3x) which made tiered dramatically better. The right approach is still tiered — the rare sessions with outliers more than compensate for the normal sessions where 2x TP edges ahead.

---

## P&L Simulation — Worst Case (Hard Failures + Near-Misses → $0)

| Strategy | Winners Return | Losses (→ $0) | Total | P&L | ROI |
|---|---|---|---|---|---|
| ATH exit | 3.074 SOL | 0 SOL | 3.074 SOL | **+0.474 SOL** | **+18%** |
| 2x take-profit | 2.000 SOL | 0 SOL | 2.000 SOL | **−0.600 SOL** | **−23%** |
| Tiered exit | 2.182 SOL | 0 SOL | 2.182 SOL | **−0.418 SOL** | **−16%** |

Even in worst case, ATH exit stays green (+18%) because the 10 winners average 3.07x. Both 2x TP and tiered go negative. **The stop loss is still the most important variable** — in the realistic simulations above, losers returned ~0.85–1.06x instead of zero, which is the difference between a profitable and losing book.

---

## Trader Leaderboard — April 29, 2026

**Scoring:** 1 point per coin bought in bonding curve that hit $70K+ ATH post-migration.

| Rank | Trader | Points | Winning Coins | Hit Rate |
|------|--------|--------|---------------|----------|
| 🥇 1 | dv | 6 | BROS, Garlic Dog, chadhouse, sam moonman, OpenAI Coin, TerminAItor | 6/11 (55%) |
| 🥈 2 | parsiix | 4 | Actually Useless, Garlic Dog, sam moonman, Frok | 4/5 (80%) |
| 🥉 3 | chester | 3 | BROS, Garlic Dog, chadhouse | 3/6 (50%) |
| 4 | theo | 2 | BROS, Frok | 2/2 (100%) |
| 5 | kevnszn | 1 | Mr. Nice Guy | 1/3 (33%) |
| 5 | west | 1 | OpenAI Coin | 1/2 (50%) |
| 5 | trenchman | 1 | Ewun Mogman | 1/5 (20%) |
| 5 | jijo | 1 | Garlic Dog | 1/2 (50%) |
| — | errol | 0 | — | 0/5 (0%) |
| — | nosa1x | 0 | — | 0/2 (0%) |
| — | decu | 0 | Psyop (❌) | 0/1 (0%) |
| — | leck | 0 | — | 0/1 (0%) |
| — | bandit | 0 | — | 0/1 (0%) |

---

## Combined Leaderboard — Apr 27–29, 2026

| Rank | Trader | Apr 27–28 | Apr 29 | Combined | Combined Rate |
|------|--------|-----------|--------|----------|---------------|
| 🥇 1 | **dv** | 5 | 6 | **11** | ~57% |
| 🥈 2 | **parsiix** | 2 | 4 | **6** | ~67% |
| 🥉 3 | **chester** | 2 | 3 | **5** | ~45% |
| 4 | **theo** | 2 | 2 | **4** | ~67% |
| 5 | kevnszn | 2 | 1 | 3 | ~38% |
| 6 | trenchman | 1 | 1 | 2 | ~25% |
| 7 | decu | 1 | 0 | 1 | — |
| 7 | west | 0 | 1 | 1 | — |
| 7 | jijo | 0 | 1 | 1 | — |

**Tier 1 traders (most reliable):** dv (11 wins), parsiix (6 wins, 67% rate), theo (4 wins, 67% rate)
**Tier 2 traders (consistent):** chester (5 wins, 45% rate), kevnszn (3 wins)
**Tier 3 traders (emerging):** trenchman, west, jijo — too few data points
**Noise traders:** errol (0/5), nosa1x (0/2), leck (0/1), bandit (0/1)

---

## Cross-Session Comparison

| Metric | Apr 27–28 | Apr 29 | Trend |
|--------|-----------|--------|-------|
| Total alerts | 31 | 26 | ↓ fewer alerts |
| Win rate | 32% (10/31) | 38% (10/26) | ↑ improved |
| EXTREME win rate | 30% (3/10) | 57% (4/7) | ↑ significantly improved |
| STALLED win rate | 40% (2/5) | 20% (1/5) | ↓ regressed to mean |
| Avg winner peak MC | $140K | $102K | ↓ smaller winners |
| Biggest winner | Vesting $307K | Actually Useless $224K | ↓ no 9x+ runner |
| Unique traders | 8 | 13 | ↑ wider tracker net |
| ROI (ATH exit) | +110% | +91% | ↓ slightly lower |
| Copy token failures | Dog In Vest | agent tusk #2 | Same pattern |

**The detector is getting more accurate** (38% vs 32%) while seeing fewer total alerts. Quality over quantity. The main weakness this session: no breakout 5x+ runner except Actually Useless, which caps the upside on every strategy.

---

## Suggestions for Improving Alert Quality (Updated)

### From Apr 27–28 (validated by Apr 29):

1. ✅ **Name blacklist** — VAMPCOIN would have been caught by a "vamp" check (vampire ≈ scam-adjacent). Consider expanding: `["scam", "rug", "ponzi", "exploit", "drain", "vamp"]`
2. ✅ **Duplicate name detector** — Agent Tusk appeared twice. Second was a STALLED copy that failed.
3. ✅ **Surface total BC SOL** — This session confirms: high total SOL (9+ across 2+ traders) correlated with winners.

### New from Apr 29:

4. **Add trader-level weighting to alerts.** parsiix (80%), theo (100% this session), and dv (55%) are categorically more reliable than errol (0%) or nosa1x (0%). Weight the alert priority by trader quality:
   - Tier 1 trader (dv, parsiix, theo) → **ELEVATED** priority
   - Tier 2 (chester, kevnszn) → standard priority
   - Unknown/new trader → **reduced** priority until track record established

5. **Flag errol as a noise trader.** 0/5 this session. If errol is the only known trader in BC → deprioritize or suppress the alert.

6. **Track VERY_FAST as a distinct tier.** OpenAI Coin was the only VERY_FAST alert and it won. The tier appears between EXTREME and FAST. Need more data to assess whether VERY_FAST is reliably high quality or this was a one-off.

---

## Key Takeaways

1. **38% overall win rate** — 10/26 alerts resulted in 2x+, up from 32%
2. **dv is still #1** — 6 winners, but now has confirmed failures when narrative is weak
3. **parsiix is the most accurate** — 80% hit rate this session, 67% combined
4. **EXTREME improved** — 57% win rate when supported by high total SOL and narrative
5. **Copy tokens confirmed** — Agent Tusk duplicate failed, same as Dog In Vest pattern
6. **errol is noise** — 0/5, consider filtering when solo
7. **Stop loss remains critical** — worst-case simulations go negative without it
8. **No session-defining outlier** — biggest winner was 6.78x vs previous session's 9.3x (or 485x SCAM)

---

## Related

- [[patterns/alert-outcomes-apr27-28]] — Apr 27–28 analysis (31 alerts)
- [[patterns/hard-failure-postmortem-apr2026]] — loser case study validating Winner Checklist
- [[patterns/winner-checklist]] — go/no-go decision framework
- [[patterns/narrative-triggers]] — narrative tier list and scoring
- [[patterns/migration-speed-signal]] — speed tier definitions
