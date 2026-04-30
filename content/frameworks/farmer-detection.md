---
name: Farmer Detection Framework
type: framework
tags: [framework, system-design]
---

# Farmer Detection Framework

> **⚠️ Data confidence: LOW–MEDIUM** — Farmer classifications (Cented, Domy) are based on a single day's data and one month's aggregate. The framework logic is sound; individual verdicts should be re-evaluated monthly. See [[traders/cented]] for updated Cented profile.

## Summary

**Traders who farm copy traders have a distinct pattern: unrealistic win rates combined with high visibility and extreme short holds.** Real skilled traders maintain realistic win rates (50-60%) even with fast execution. This framework helps distinguish between sustainable trading edges and exploitative farming strategies.

---

## What is a "Farmer"?

A **farmer** is a trader who:

1. Builds a public profile (leaderboard ranking, high visibility)
2. Attracts copy traders to follow their trades
3. Executes trades very quickly (7-10 seconds)
4. **Exits BEFORE copy traders' orders fill**
5. Profits from the **spread created by copy traders**, not from actual trading edge

### The Farmer Mechanism

```
T=0s:   Farmer buys 100 SOL of token X
T=1s:   Leaderboard updates (farmer shows +5% profit)
T=2s:   Copy traders see the signal
T=3s:   Copy traders start buying (placing orders)
T=5s:   Token price rises due to copy volume
T=7s:   FARMER EXITS (sells at peak)
T=10s:  Copy traders' buys finally fill (at high price)
T=20s:  Token dumps (initial buying pressure exhausted)
T=30s:  Copy traders are underwater
```

**Result:** Farmer made +5%, copy traders made -2%. Farmer profited FROM copy traders, not WITH them.

---

## Red Flags: How to Spot a Farmer

### 🚩 RED FLAG #1: Unrealistic Win Rate

|Win Rate|Hold Time|Interpretation|
|---|---|---|
|90%+|Any|🚨 **FARMER** (statistically impossible)|
|75%+|< 30s|🚨 **FARMER** (too high for scalping)|
|60-70%|< 30s|⚠️ **SUSPICIOUS** (verify other flags)|
|50-60%|< 30s|✅ **REALISTIC** (possible with real edge)|
|40-50%|Any|✅ **REALISTIC** (normal trading range)|

**Why?** At extreme speeds (7-10 seconds), even the best traders face execution risk. A 94.6% win rate is statistically implausible unless the edge comes from copy traders (farming), not from market movements.

**Real Data Evidence:**

- theo: 55.9% win rate = **REALISTIC** *(hold time disputed — see note below)*
- radiance: 54.45% win rate = **REALISTIC**
- Cented: 94.6% win rate = **UNREALISTIC** 🚨

> **⚠️ Data Conflict — theo's hold time:** This page originally cited "7-second holds" for theo (sourced from Theo_Live_Trade_Analysis, a 99-minute on-chain snapshot on Apr 22). The operational strategy pages (Theo_Exit_Rules, Theo_Step_by_Step_Guide) describe 30–60 second holds. The Theo_Front_Run_Strategy analysis shows 30–60 sec as the average. The 7-second figure may reflect a subset of very fast trades or a measurement artifact. **Treat theo's hold time as 7–60 seconds depending on trade type; the 55.9% win rate is consistent across sources.**

---

### 🚩 RED FLAG #2: High Visibility + Leaderboard Dominance

|Metric|Farmer Signal|Skill Signal|
|---|---|---|
|Daily Rank|#1, #2 (very high)|#9, #20, #25 (lower)|
|Broadcast Hold Time|YES (brags about speed)|NO (keeps it private)|
|Social Media Presence|High (recruits copy traders)|Low (doesn't need them)|
|Mentions of "Copy Me"|Explicit|Never mentioned|

**Why?** Farmers NEED copy traders to farm. They attract visibility. Skilled traders don't need farmers — their edge works independently.

**Real Data Evidence:**

- Cented: #1 daily + #1 monthly = **FARMING SIGNAL** *(10-second hold time asserted; no direct on-chain verification in raw data)*
- theo: #9 daily → #2 monthly, **hold time not broadcast** = **SKILL SIGNAL**
- radiance: #8 daily → #20 monthly, **quiet profile** = **SKILL SIGNAL**

---

### 🚩 RED FLAG #3: Daily Spike → Monthly Fade

|Pattern|Interpretation|
|---|---|
|#1 daily, #1 monthly|✅ Consistent skill OR farming both|
|#1 daily, #50 monthly|🚨 **FARMER** (daily edge doesn't compound)|
|#2 daily, #27 monthly|🚨 **FARMER** (ranking collapsed)|
|#9 daily, #2 monthly|✅ **SKILL** (slow-building edge)|
|#8 daily, #20 monthly|✅ **SKILL** (sustainable)|

**Why?** Real edges compound monthly. Farming edges collapse monthly (copy traders adapt, find new farmers).

**Real Data Evidence:**

- Domy: Daily #2 → Monthly #27 (25-position drop) = **FARMER**
- theo: Daily #9 → Monthly #2 (rank improved) = **SKILL**

---

### 🚩 RED FLAG #4: Win Rate Doesn't Improve with Scale

|Trader|Daily Win %|Monthly Win %|Trend|Signal|
|---|---|---|---|---|
|Cented|47.4%|94.6%|**DOUBLED**|⚠️ Suspicious (improved too much)|
|theo|~56%|55.9%|**Flat**|✅ Realistic (consistent)|
|radiance|43.5%|54.45%|**Slight improvement**|✅ Realistic (normal learning)|

**Why?** Real traders improve 2-10% with scale (better execution, learning). Farmers show extreme swings (47% → 95%) = they're exploiting copy traders differently daily/monthly.

---

### 🚩 RED FLAG #5: Extreme Short Holds ONLY

|Trader|Hold Times|Pattern|Signal|
|---|---|---|---|
|Farmer|All 5-15s|**Never varies**|🚨 **FARMING** (can't adapt)|
|Skilled|Mix (5s, 30s, 2m)|**Adapts to market**|✅ **SKILL** (flexibility)|

**Why?** Real traders adapt to market conditions. Farmers are locked into the 5-15s window (where copy traders take time to fill). If they held longer, copy traders would catch up.

**Real Data Evidence:**

- theo: 7s hold, but portfolio shows variation (different tokens, different timing) = **SKILL**
- Cented: Strict 10s holds, always exits at that window = **FARMING PATTERN**

---

## The Farmer Detection Checklist

**Score 1 point for each red flag:**

### Trader Analysis Template

**Trader Name:** _______________

```
[ ] 1. Win Rate: Is it 75%+ on fast holds (< 30s)?
      (90%+ = automatic farmer flag)

[ ] 2. Visibility: Are they #1-3 on leaderboards?
      (Do they broadcast hold times to attract copy traders?)

[ ] 3. Daily vs Monthly: Did daily rank drop >10 spots monthly?
      (e.g., #2 daily → #27 monthly)

[ ] 4. Consistency: Did win rate jump >20% from daily to monthly?
      (47% → 95% = farming signal)

[ ] 5. Flexibility: Do they only hold 5-15 seconds?
      (No variation = farming lock)

SCORE: ___ / 5

0-1 points: ✅ REAL SKILL (safe to copy)
2-3 points: ⚠️ SUSPICIOUS (investigate more)
4-5 points: 🚨 FARMER (do not copy)
```

---

## Case Studies: Real Examples

### ✅ CASE STUDY #1: THEO (Real Skill)

```
Win Rate: 55.9% monthly ✅ REALISTIC
Visibility: #9 daily, #2 monthly ✅ NOT CHASING #1
Hold Time: 7–60 seconds (source-dependent) ✅ WITHIN REALISTIC RANGE
Daily → Monthly: Improved ✅ SKILL
Flexibility: Portfolio varies ✅ ADAPTABLE

Score: 0/5 → REAL SKILL ✅
```

**Conclusion:** theo's edge is real execution, not farming. Safe to copy. Hold time varies by data source (7s from on-chain snapshot vs 30–60s from strategy docs); win rate is consistent at 55–59% across all sources.

---

### ✅ CASE STUDY #2: RADIANCE (Real Skill)

```
Win Rate: 54.45% monthly ✅ REALISTIC
Visibility: #8 daily, #20 monthly ✅ LOW PROFILE
Hold Time: 8 seconds ✅ CONSISTENT
Daily → Monthly: Stable ✅ SUSTAINABLE
Flexibility: Portfolio shows variety ✅ ADAPTABLE

Score: 0/5 → REAL SKILL ✅
```

**Conclusion:** radiance is a steady professional. Edge is real. Safe to copy.

---

### 🚨 CASE STUDY #3: CENTED (Likely Farmer)

```
Win Rate: 94.6% monthly 🚨 UNREALISTIC
Visibility: #1 daily, #1 monthly 🚨 MAXIMUM VISIBILITY
Hold Time: 10 seconds (published) 🚨 BROADCASTS FOR FARMERS
Daily → Monthly: Both #1 🚨 MAINTAINS #1 (farming advantage)
Flexibility: All 10-second holds 🚨 LOCKED PATTERN

Score: 5/5 → LIKELY FARMER 🚨
```

**Conclusion:** Cented's 94.6% win rate is too high to be real skill. Likely exploiting copy traders. Risky to copy.

---

### 🚨 CASE STUDY #4: LUKEY (Likely Farmer)

From monthly leaderboard (rank #30):

```
Win Rate: 96.4% (27 wins / 1 loss) 🚨 STATISTICALLY IMPOSSIBLE
Monthly PnL: +94.12 SOL (low absolute PnL despite perfect record)
Visibility: Ranked monthly #30 ⚠️ MODERATE (building profile)
Hold Time: Unknown — insufficient data
Daily Appearance: Not in daily top 30 ⚠️ INCONSISTENT

Score: 3/5 → LIKELY FARMER 🚨
```

**Conclusion:** 27/1 win rate over a 30-day period is mathematically implausible for market-based trading. The low absolute PnL (+94 SOL despite 96% win rate) suggests small position sizes — consistent with early-stage farming while building a follower base. Monitor for ranking increase and win rate decline as farming saturates.

---

### ⚠️ CASE STUDY #5: WUGI (Suspicious)

From monthly leaderboard (rank #17):

```
Win Rate: 73.1% (19 wins / 7 losses) ⚠️ ELEVATED
Monthly PnL: +246.77 SOL
Visibility: Ranked monthly #17 ⚠️ MODERATE VISIBILITY
Hold Time: Unknown — insufficient data
Daily Appearance: Not in daily top 30 — no cross-platform check available

Score: 2/5 → SUSPICIOUS ⚠️
```

**Conclusion:** 73% monthly win rate clears the farming suspicion threshold (75%+) by a narrow margin. Insufficient data to confirm. Needs hold time data and daily/monthly cross-check before copying. Treat as suspicious until more data available.

---

## Why Farmers Eventually Fail

### The Farmer Lifespan

```
PHASE 1: Growth (Weeks 1-4)
- Trader builds profile
- Attracts first copy traders
- Farming edge works (spreads are juicy)
- Win rate: High (94%+)
- Copy traders: Happy (early followers do well)

PHASE 2: Saturation (Weeks 5-12)
- More copy traders follow
- Orders fill faster (less spread to farm)
- Edge narrows
- Farmer has to trade faster/more aggressively
- Win rate: Starts declining

PHASE 3: Collapse (Weeks 13+)
- Copy traders figure out they're being farmed
- Exit trades early (front-run the farmer)
- Farmer's edge disappears
- Win rate: Crashes to 20-30%
- Monthly ranking: Drops to #50+
- Copy traders: Abandon (lost money)
```

**Result:** Farmer's returns unsustainable. Real skill (theo, radiance) compounds. Farmers fade.

---

## The Skill vs Farmer Win Rate Gap

### Why This Matters

**Real skilled trader at 8-second holds:**

- Win rate: 55%
- Loses 45% of trades (real market risk)
- Edge: Comes from better timing, entry accuracy, risk management
- Sustainable: Yes (works regardless of copy traders)

**Farmer at 8-second holds:**

- Win rate: 94%
- Loses only 6% of trades (impossible without farming)
- Edge: Comes from exploiting copy trader fills
- Sustainable: No (collapses when copy traders leave)

**The Math:**

- 55% win rate at 8s = realistic (market noise, execution risk)
- 94% win rate at 8s = farming (copy traders create the spread)

---

## How to Verify Your Assessment

### Tier 1: Score the Checklist (0-5)

Use the template above. Score 4-5 = likely farmer.

### Tier 2: Analyze Win Rate Math

- Calculate expected win rate for the hold time
- 8-second holds should be 45-60% max
- 90%+ = automatic red flag

### Tier 3: Track Over Time

- Watch the trader for 2-4 weeks
- Do rankings change?
- Does win rate decline?
- Farmers will show:
    - Win rate declining
    - Monthly rank dropping
    - Copy traders leaving

### Tier 4: Check Community Feedback

- Are copy traders complaining about fills?
- Are they talking about "farming"?
- Do experienced traders avoid this trader?

---

## Actionable Rules

### ✅ SAFE TO COPY (Real Skill)

1. Win rate 40-60% on any hold time
2. Win rate 50-65% on short holds (< 30s)
3. Daily rank ≠ Monthly rank (skill improves with scale)
4. Low visibility (not trying to recruit copy traders)
5. Hold times vary (adaptable to market)

### 🚨 DO NOT COPY (Likely Farmer)

1. Win rate 75%+ on any hold time
2. Win rate 90%+ on short holds (statistically impossible)
3. #1-2 daily AND #1-2 monthly (farming advantage)
4. Broadcasts hold times (recruits copy traders)
5. All trades in 5-15 second window (locked pattern)

### ⚠️ INVESTIGATE FURTHER (Suspicious)

1. Win rate 65-75% on short holds
2. Daily #1 OR monthly #1, but not both
3. Medium visibility (some recruitment)
4. Recent entrant to leaderboard (unproven)
5. Portfolio shows zero losses (impossible)

---

## The Key Insight

**Real traders show realistic statistics.** **Farmers show impossible statistics.**

The difference between theo (55.9% win rate) and Cented (94.6% win rate) on similar hold times is not experience — it's that theo trades against the market, Cented trades against copy traders.

---

## Final Checklist: Before You Copy Anyone

```
[ ] Win rate makes mathematical sense for hold time?
[ ] Daily/monthly rankings are consistent or improving?
[ ] Trader doesn't broadcast speed or attract copy traders?
[ ] Win rate is stable or improving (not declining)?
[ ] Portfolio shows adaptation (not locked pattern)?
[ ] Been profitable for 30+ days?
[ ] Monthly ranking is top 50 (proven over time)?

If all YES → Copy this trader
If any NO → Investigate further
```

---

## Sources

- axiom_trades_apr22.txt
- kol_scan_daily_apr22.txt
- kol_scan_monthly_apr22.txt
- Cielo trader profiles (hold time data)

## Related Pages

- [[traders/theo]] — Real skill example (55.9% win rate, sustainable)
- [[traders/cented]] — Farmer example (94.6% win rate, suspicious pattern)
- [[patterns/winner-checklist]] — Complementary signal validation framework
- [[playbooks/theo-style]] — How skilled traders execute