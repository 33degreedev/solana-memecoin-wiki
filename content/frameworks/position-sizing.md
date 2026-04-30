---
name: Position Sizing and Volume Efficiency
type: framework
tags: [framework, system-design]
---

# Position Sizing and Volume Efficiency

## Summary

**Fewer positions + lower trade churn = dramatically higher capital efficiency.** Classic generates 185% return on volume while chingchongslayer generates 0.09% — a 2,000x gap. Position concentration (not position count) is the primary driver of sustainable PnL. High volume is a red flag for capital erosion, not a sign of edge.

---

## Volume Efficiency: PnL as % of Volume Traded

Volume efficiency = PnL ÷ Volume moved. Measures how much value a trader extracts per unit of capital deployed.

| Trader | PnL (SOL) | Volume (SOL) | PnL/Volume | Hold Time | Strategy |
|--------|-----------|--------------|------------|-----------|----------|
| Classic | +793 | 427.5 | **185.6%** | 40m | Focused, few large bets |
| Pandora | +108.3 | 1,860 | 5.8% | 1m | Aggressive scalp |
| Teddy | +284.4 | 6,450 | 4.4% | 12h | Large position swings |
| Sebastian | +179.6 | 4,950 | 3.6% | 42m | Medium-term |
| Ramset | +9.549 | 387.9 | 2.5% | 1h | Long hold, low activity |
| Cultures | +14.57 | 616.5 | 2.4% | 26s | Micro-scalp |
| Qavec | +122.6 | 9,910 | 1.2% | 33m | Medium-high activity |
| Domy | +101.8 | 9,010 | 1.1% | 1m | Ultra-scalp |
| chingchongslayer | +161 | 172,000 | **0.09%** | 14m | Extreme frequency |

**Key finding:** Classic moves 427 SOL of volume to make 793 SOL profit. chingchongslayer moves 172,000 SOL of volume to make 161 SOL profit. Classic needs 540x less capital throughput for 5x the PnL.

---

## Position Concentration: Trades per Position

Trades/Positions ratio measures how many times a trader cycles in and out per unique token. Lower = more conviction per entry.

| Trader | Positions | Trades | Trades/Position | PnL/Volume | Interpretation |
|--------|-----------|--------|-----------------|------------|----------------|
| Classic | 123 | 270 | **2.2** | 185.6% | Clean in-out, high conviction |
| Cultures | 119 | 328 | 2.8 | 2.4% | Few tokens, low efficiency |
| Ramset | 55 | 202 | 3.7 | 2.5% | Low activity, poor edge |
| Sebastian | 690 | 2,930 | 4.2 | 3.6% | Moderate churn |
| Pandora | 244 | 1,140 | 4.7 | 5.8% | Decent focus |
| Teddy | 1,060 | 5,430 | 5.1 | 4.4% | High position count |
| Domy | 1,170 | 6,180 | 5.3 | 1.1% | Scattered |
| Qavec | 1,940 | 13,200 | 6.8 | 1.2% | High churn |
| chingchongslayer | 4,240 | 175,000 | **41.3** | 0.09% | Extreme scatter |

**Pattern:** Traders with Trades/Position < 3 show higher volume efficiency. Above 5, efficiency collapses. Classic at 2.2 represents the theoretical minimum — nearly one entry and one exit per token.

---

## The Concentration Hypothesis

Classic's numbers suggest a distinct approach:
- 123 positions, 270 trades → nearly binary (one buy, one sell per token)
- Selects tokens with high conviction, exits cleanly
- Does NOT re-enter, average down, or add to winners

chingchongslayer's numbers suggest:
- 41+ actions per position (averaging in/out, multiple partial exits)
- Edge per action is near-zero (0.09% volume efficiency)
- Scale compensates for low edge quality — unsustainable in slow markets

**Implication:** High trades-per-position is a signal of poor entry conviction, not sophisticated execution.

---

## Does More Positions = More PnL?

| Positions (count) | Trader | PnL | PnL/Volume |
|-------------------|--------|-----|------------|
| 55 | Ramset | +9.5 | 2.5% |
| 119 | Cultures | +14.6 | 2.4% |
| **123** | **Classic** | **+793** | **185.6%** |
| 244 | Pandora | +108.3 | 5.8% |
| 690 | Sebastian | +179.6 | 3.6% |
| 1,060 | Teddy | +284.4 | 4.4% |
| 1,170 | Domy | +101.8 | 1.1% |
| 1,940 | Qavec | +122.6 | 1.2% |
| 4,240 | chingchongslayer | +161 | 0.09% |

**Finding:** No linear relationship between position count and PnL. Classic (123 positions) outperforms Teddy (1,060 positions) by 2.8x in total PnL and 42x in volume efficiency. Position count is irrelevant; position quality is everything.

---

## The Outlier: Classic

Classic's metrics are anomalous relative to the rest of the dataset:

- Volume efficiency: 185.6% vs next-best 5.8% (32x gap)
- Trades/Position: 2.2 (nearest peer: Cultures at 2.8)
- Total PnL: #1 in dataset (+793 SOL)
- Win rate: 50.41% (not extreme — realistic skill)
- Hold time: 40m (within the sweet spot)

**Hypothesis:** Classic has a precise token-selection system that generates outsized wins per trade. The low trade count (270) and low position count (123) relative to volume moved (427.5 SOL) suggests large per-position sizing. Classic may be betting 2-4 SOL per position vs 0.01-0.5 SOL for scalpers.

Note: Classic does not appear on KOL Scan leaderboards (daily or monthly), which require high trade frequency for ranking. High-quality, low-frequency trading is invisible to volume-based leaderboards.

---

## Actionable Rules

### Position Sizing
- ✅ Limit to 100-300 active positions per month (not 1,000+)
- ✅ Target Trades/Position < 3 (clean entries and exits)
- ✅ Size larger on fewer, higher-conviction tokens
- ❌ Do not average down or re-enter losing positions (drives Trades/Position up)
- ❌ Do not diversify into 1,000+ positions (kills capital efficiency)

### Volume Efficiency Targets
- ✅ Aim for >3% PnL/Volume (achievable with discipline)
- ✅ Track your own Trades/Position weekly
- ❌ If Trades/Position > 6, review entry conviction criteria
- ❌ If PnL/Volume < 1%, reduce trade frequency and increase position size

---

## Sources

- axiom_trades_apr22.txt
- ANALYSIS_PLAN.txt (Position Sizing Pattern + Volume Efficiency questions)

## Related

- [[traders/theo]] — Trader with proven position sizing discipline
- [[playbooks/theo-style]] — 5% position sizing rule in practice
- [[frameworks/farmer-detection]] — How position count relates to farming signals
- [[frameworks/trade-deconstruction]] — Understanding sizing patterns through deconstruction
