---
title: "Trade Deconstruction Framework: Learn to Fish, Not Copy"
name: "Trade Deconstruction Framework: Learn to Fish, Not Copy"
type: framework
tags: [framework, system-design]
---

# Trade Deconstruction Framework: Learn to Fish, Not Copy

## Executive Summary

Instead of copying trades, this framework teaches you to **dissect each trade like a surgeon**, understand WHY the trader made it, WHEN they knew to exit, and WHAT signals they used. By reverse-engineering 50-100 trades, you'll internalize the edge and trade independently.

---

## **THE PRINCIPLE: Deconstruction Over Imitation**

### Copy Trading (Temporary)

```
theo makes trade → You copy → Price goes up/down → You follow exit
Result: 55% win rate (theo's), -5% slippage (yours) = 50% win rate
Sustainability: 0 (depends on theo forever)
```

### Trade Deconstruction (Permanent)

```
theo makes trade → You deconstruct it → Understand entry/exit/sizing
→ Find similar pattern → Apply independently → Build your own edge
Result: 45-50% win rate (your skill) → 60%+ over time (learning curve)
Sustainability: ∞ (you own the edge)
```

---

## **PHASE 1: TRADE COLLECTION (Days 1-7)**

### Goal

Capture 20-30 of theo's trades with **complete data**.

### What to Capture for EACH Trade

```
TRADE LOG TEMPLATE:

Trade #1:
├── Entry
│   ├── Token: [name/address]
│   ├── Entry price: $0.00125
│   ├── Entry time: 2026-04-22 14:33:22 UTC
│   ├── Entry size: [theo's position]
│   ├── Entry source: Where did theo find this token?
│   │   └── (Birdeye new launch? Twitter mention? Community?)
│   └── Entry signal: What triggered the buy?
│       └── (Volume spike? Whale movement? Price action?)
│
├── During Trade
│   ├── Hold time: 7–60 seconds (this example: 7s — a fast exit trade)
│   ├── Price movement: +5% (peak) at T=5s
│   ├── Volume during hold: [increasing/stable/decreasing]
│   └── Competitor activity: [other wallets buying/selling?]
│
├── Exit
│   ├── Exit price: $0.00131
│   ├── Exit time: 2026-04-22 14:33:29 UTC
│   ├── Exit signal: What made theo exit?
│   │   └── (Time-based? Price target? Volume drop?)
│   ├── Profit: +4.8%
│   └── Exit reason: Why this exact moment?
│
└── Metadata
    ├── Win/Loss: ✅ Win
    ├── Slippage: 0.5%
    ├── Gas fees: 0.00005 SOL
    ├── Net PnL: +4.2%
    └── Pattern: [Early momentum, exit on peak, perfect timing]
```

### How to Capture This Data

#### **Step 1: Find theo's wallet on Solscan**

1. Get theo's wallet address (from Cielo or Twitter bio)
2. Go to Solscan.io
3. Search wallet
4. Go to "Transactions" tab
5. Filter for last 7 days

#### **Step 2: Identify theo's trades**

Look for:

- ✅ **Buy**: Wallet sends SOL → receives SPL token
- ✅ **Sell**: Wallet sends SPL token → receives SOL back
- ❌ **Ignore**: Internal transfers, staking, swaps for other SPL tokens

#### **Step 3: For each buy-sell pair, record**

**From Solscan transaction page:**

```
- Token address (click token to get details)
- Entry time (from "Confirmed" timestamp)
- Entry size (click transaction → see "Amount In")
- Exit time (find matching sell transaction)
- Exit size (verify same token address)
- Entry price = (SOL spent / tokens received)
- Exit price = (SOL received / tokens sold)
- Profit = ((Exit price - Entry price) / Entry price) × 100
```

**From DexScreener or Birdeye (cross-check):**

- Current token price
- Token age (when launched)
- Volume at entry time vs exit time
- Holder count change
- Liquidity at entry/exit

#### **Step 4: Document the context**

For each trade, search Twitter/Reddit:

```
"[Token name] solana" on Twitter
- When was it mentioned?
- Who mentioned it? (influencers? random users?)
- What sentiment? (hype? FUD?)
- Was theo first to enter or late?
```

**Result:** 20-30 trades with complete entry/exit/context data.

### Tools Needed

- Solscan.io (free)
- DexScreener (free)
- Birdeye (free)
- Twitter search (free)
- Spreadsheet (Google Sheets, Excel, or Obsidian table)

### Time Investment

- 2-3 hours total
- ~5-10 min per trade

---

## **PHASE 2: PATTERN RECOGNITION (Days 8-14)**

### Goal

Find the **repeating patterns** in theo's 30 trades.

### The 5 Core Questions

#### **Q1: ENTRY PATTERNS — How does theo find tokens?**

**Analysis:** For each of theo's 30 trades, note:

- When was token launched? (< 1 hour old? 1-24 hours?)
- Token age at theo's entry: _____ minutes old
- Where did theo learn about it?
    - [ ]  Birdeye trending
    - [ ]  Twitter mention
    - [ ]  Discord/Telegram alert
    - [ ]  Community discussion
    - [ ]  Price action/volume (found organically)

**The Pattern:**

```
Hypothesis: theo enters tokens 5-15 minutes old

Test:
30 trades analyzed:
- 18 trades: Token age 5-12 min ✅ (60%)
- 8 trades: Token age 13-30 min ✅ (27%)
- 4 trades: Token age > 30 min ❌ (13%)

Conclusion: theo has a 5-15 minute sweet spot for entry
```

**Key Insight:** If theo mostly enters young tokens, their edge is **speed + early identification**, not deep analysis.

---

#### **Q2: ENTRY SIGNALS — What does theo look for at entry?**

**Analysis:** For each trade, identify the trigger:

```
Trade #1: PUMP token
Entry price: $0.00125
Entry size: 2.5 SOL
Signal checklist:
  ├── Volume spike in last 5 min? YES (+200%)
  ├── New large buy? YES (0.5 SOL whale entry)
  ├── Holder count increasing? YES (12 → 34 holders)
  ├── Influencer mention? NO
  ├── Price already +10%? YES (+12% from launch)
  └── Liquidity > $50k? YES ($85k)

Primary signal: VOLUME SPIKE + WHALE BUY
Secondary signal: New holders growing fast
Tertiary signal: Decent liquidity
```

**Pattern across 30 trades:**

```
Volume spike: 28/30 (93%) 🔴 STRONGEST SIGNAL
Whale buy: 24/30 (80%) 🔴 STRONG SIGNAL
Influencer mention: 8/30 (27%) ⚠️ WEAK SIGNAL
Chart pattern: 12/30 (40%) ⚠️ MODERATE
Community hype: 5/30 (17%) ⚠️ NOISE

Conclusion: theo's edge is VOLUME + WHALE detection
theo is a momentum/whale-follower, not a technician
```

**Key Insight:** theo is riding **early momentum**, not finding hidden gems. This is important — it means theo's edge requires:

1. Real-time data feeds (volume, whale movements)
2. Fast reaction time (7s holds)
3. Ability to spot micro-trends (minute-level volume)

---

#### **Q3: SIZING PATTERNS — How much does theo risk per trade?**

**Analysis:** For each trade, calculate:

```
Trade #1:
- Starting balance (visible on wallet): 85 SOL
- Entry size: 2.5 SOL
- Risk % of balance: (2.5 / 85) × 100 = 2.9%
- Win/Loss: +4.2%
- PnL amount: +0.105 SOL

Trade #2:
- Starting balance: 89.1 SOL
- Entry size: 1.8 SOL
- Risk %: 2.0%
- Win/Loss: -6.1%
- PnL amount: -0.11 SOL
```

**Pattern across 30 trades:**

```
Average risk per trade: 2.1% of balance ✅
Min risk: 0.8% (tiny loss trade)
Max risk: 4.5% (big win trade)
Std deviation: 0.8% (consistent)

Win trades avg size: 2.3%
Loss trades avg size: 1.9%

Conclusion: theo sizes BIGGER on wins (confident), SMALLER on losses (humble)
BUT sizes are always 1.5%-3% range = disciplined risk management
```

**Key Insight:** theo risks ~2% per trade. Over 50 trades:

- Expected: 55% × 2% = +1.1% / trade
- 30 trades × 2% = 60% of balance at risk (diversified)
- Actual results: ✅ Matches data

---

#### **Q4: EXIT PATTERNS — How does theo know when to exit?**

**THIS IS THE GOLDEN QUESTION.** Exit is where the edge lives.

**Analysis:** For each trade, record:

```
Trade #1: PUMP token
Entry: $0.00125
Exit: $0.00131
Exit time: 7 seconds after entry
Exit signal: ?

Analyze exit:
  ├── Exit at price target? +4.8% (does theo have a rule like +5%?)
  ├── Exit on time? YES (exactly 7 seconds)
  ├── Exit before volume died? YES (volume still 150% of entry volume)
  ├── Exit before whale left? YES (whale position still growing)
  ├── Exit on specific indicator? (check chart at T=7s)
  └── Exit reason: TIMING (not price target, just a hard 7s rule)
```

**Pattern across 30 trades:**

```
Exit type breakdown:
1. Time-based exit (7 seconds hard stop): 22/30 (73%) 🔴
2. Price target exit (+4-6% profit): 5/30 (17%)
3. Volume-based exit (volume drops): 2/30 (7%)
4. Forced exit (slippage too high): 1/30 (3%)

Conclusion: theo uses a TIMER, not a price target
theo exits after ~7 seconds regardless of profit
```

**This is HUGE.**

**What this reveals:**

- theo isn't waiting for perfect price targets
- theo is exploiting a 7-second momentum window
- After 7s, the edge deteriorates (copy traders fill in)
- theo is essentially saying: "I have 7s to profit before the market reprices"

**Why 7 seconds?**

- Time for copy traders to notice the trade
- Time for their orders to fill (network latency + DEX)
- Optimal exit before their volume deflates the price

---

#### **Q5: LOSS PATTERNS — How does theo prevent cascading losses?**

**Analysis:** Identify theo's 5-10 LOSS trades:

```
Loss Trade #1:
Entry: $0.00125 (2.5 SOL)
Exit: $0.00118
Exit time: 6 seconds after entry (EARLY EXIT!)
Loss: -5.6%

Why exit early?
  ├── Price fell -2% at T=3s
  ├── Volume started declining at T=4s
  ├── Whale didn't follow (no new buys)
  └── theo exited to prevent -8%, -10%, -15% loss

Loss Trade #2:
Entry: $0.00125
Exit: $0.00119
Exit time: 8 seconds (LATE EXIT)
Loss: -4.8%

Insight: Even on losses, theo exits within 6-9 seconds
```

**Pattern for losses:**

```
Average loss trade exit time: 6.2 seconds (vs 7.1s for wins)
Loss trades held slightly SHORTER = quick cut
Biggest loss: -6.1%
Win trades average: +4.8%

Win/Loss ratio: +4.8% / -5.8% ≈ 0.83
This means theo loses ~same % as he wins
But 55% win rate makes it profitable
```

**Key Insight:** theo's edge ISN'T:

- ❌ Bigger wins than losses
- ❌ Perfectly timed exits
- ❌ Avoiding losses

**theo's edge IS:**

- ✅ 55% accuracy on entry signals
- ✅ Fast, disciplined exits (no hope)
- ✅ Consistent sizing (2% per trade)
- ✅ Exploiting a specific 7-second window

---

### Deliverable: Pattern Analysis Document

Create in Obsidian: `Theo_Trade_Deconstruction.md`

markdown

```markdown
# theo Trade Deconstruction Analysis

## Entry Pattern
- Tokens: 5-15 minutes old
- Primary signal: Volume spike (93%)
- Secondary: Whale movement (80%)
- Edge: Real-time data feeds + fast reaction

## Sizing Pattern
- Risk per trade: 2.1% of balance
- Bigger on wins: 2.3% avg
- Bigger on losses: 1.9% avg
- Strategy: Kelly criterion derivative

## Exit Pattern
- Timing: 7 seconds (hard stop)
- Profit taking: Not price-based, time-based
- Loss cutting: 6.2 seconds (slightly faster than wins)
- Strategy: Exploit copy-trader fill time

## Edge Summary
NOT: Magical pattern recognition
IS: Speed + Data + Discipline

## Can You Replicate?
- ✅ Sizing: Yes (use Kelly formula)
- ✅ Timing: Yes (set timer)
- ⚠️ Entry signals: Partially (need real-time data feeds)
- ⚠️ Speed: Hard (7s requires low latency)

## Conclusion
theo's edge is MECHANICAL, not mystical.
theo is a MOMENTUM SCALPER exploiting fill delays.
```

---

## **PHASE 3: EDGE REPLICATION (Days 15-30)**

### Goal

Trade like theo WITHOUT copying theo.

### Step 1: Identify Your Constraints vs theo

**theo's Setup:**

- ✅ Solana network access (Helius RPC or similar)
- ✅ Real-time data feeds (Birdeye, DexScreener API)
- ✅ Low-latency execution (Photon or Raydium)
- ✅ 7-second reflexes (automated or superhuman fast)
- ✅ 55% accuracy on momentum detection

**Your Setup (Realistically):**

- ❌ May not have low-latency execution
- ❌ May not have real-time Birdeye data
- ❌ May be slower (human reaction time = 200-500ms)
- ✅ Can replicate sizing (2% per trade)
- ✅ Can replicate discipline (hard stops)

### Step 2: Adapt theo's Strategy to Your Constraints

**Option A: Slower Momentum Scalping (30-60 second holds)**

Instead of 7s, you hold 30-60s:

- Entry: Same volume/whale signals
- Hold: 30-60 seconds
- Exit: When volume/momentum stalls
- Expected win rate: 45-50% (slightly lower than theo's 55%)
- Expected edge: Still real (momentum plays out slowly)

**Realistic edge:**

```
theo: 7s holds, 55% win rate, +48% monthly
You: 60s holds, 48% win rate, +18% monthly

Why lower?
- Longer holds = more volatility = more -5% losses
- But you avoid the "too fast" execution risk

Still profitable, just less explosive.
```

**Option B: Volume-Only Detection (Eliminate Whale-Watching)**

Instead of tracking whales in real-time, you use:

- DexScreener volume API (5-min updates)
- GMGN volume trending
- Birdeye trending tabs

This means you find tokens AFTER the first 15 minutes, not in the first 5 minutes:

- Entry: When volume spikes 50%+ (visible on charts)
- Hold: 5-15 minutes (more time, less pressure)
- Exit: When volume normalizes or price target hit
- Expected win rate: 45-50%
- Expected edge: +12-20% monthly (slower but achievable)

**Option C: Hybrid — Learn theo's Timing, Apply Your Pace**

```
theo's framework:
1. Find young tokens (5-15 min old)
2. Wait for volume spike
3. Enter with 2% of capital
4. Exit in 7 seconds OR when volume dies
5. Repeat

Your adaptation:
1. Find tokens on trending lists (Birdeye, DexScreener)
2. Wait for confirmed volume spike (5-min chart)
3. Enter with 2% of capital
4. Exit when volume drops 30% OR after 5 minutes
5. Repeat
```

**Expected results: +12-25% monthly** (achievable as a human trader)

---

### Step 3: Build Your Own Trade Setup

### Minimum Setup (Free/Low-Cost)

```
Tool Stack:

1. DATA COLLECTION (Free)
   ├── Birdeye.so (trending tokens)
   ├── DexScreener.com (volume charts)
   ├── Solscan.io (transaction monitoring)
   └── Twitter search (community signals)

2. ENTRY DETECTION (Free)
   ├── Watch Birdeye trending every 5 minutes
   ├── Filter for: volume > $500k, liquidity > $100k
   ├── Look for: fresh tokens + volume spike
   └── Manual check: Does theo or radiance buy this?

3. EXECUTION (Cost: $0-50)
   ├── Backpack wallet (free, Solana-native)
   ├── OR Phantom wallet (free)
   ├── Use: Raydium DEX directly (slippage calculator)
   └── Optional: Photon (faster, costs $2-5 per premium tx)

4. TRACKING (Free)
   ├── Solscan bookmark (track your wallet)
   ├── Google Sheets: Record every trade
   ├── Obsidian: Weekly analysis
   └── Telegram: Set phone alerts for target tokens

5. TIMING (Free)
   ├── Timer.net (or phone timer)
   ├── Obsidian task: "Review position at 5min mark"
   └── Discipline: No holding past 15 minutes
```

---

### Step 4: Paper Trading (Days 15-21)

**Don't use real SOL yet.** Simulate with spreadsheet:

```
PAPER TRADING LOG:

Date: 2026-04-22
Token: PUMP
Paper entry: $0.00125 (1.5 SOL = simulated)
Paper exit: $0.00131
Paper PnL: +4.8%
Slippage estimate: -0.5% (realistic)
Paper net: +4.3%
Actual theo trade (for reference): +4.2% ✅

---

Repeat 20-30 simulated trades.
Goal: Prove your entry/exit decisions match theo's accuracy.
```

**Quality Check:**

- Are your imaginary wins similar to theo's? (4-5% range)
- Are your imaginary losses similar? (-5% range)
- Is your win rate close to 50%? (theo's is 55%, your realistic is 48-50%)

**If YES:** Move to real trading. **If NO:** Identify why and adjust your rules.

---

### Step 5: Live Trading with Real Capital (Days 22-30)

**Start with 1 SOL, as planned. But now you trade theo's strategy, not theo's account.**

```
THEO'S STRATEGY REPLICATION:

Day 1: Watch, don't trade (confidence building)
Day 2: First 0.2 SOL trade (small)
Day 3: 0.3 SOL trade if up, 0.2 SOL if down
Day 4-7: 0.5 SOL trades, stack wins
Week 2: Scale to 0.7-1.0 SOL per trade

Rules:
├── Risk 2% per trade (your capital)
├── Hold 30-60 seconds (your speed)
├── Exit on volume drop OR price target
├── Never hold overnight
└── Record everything for analysis
```

---

## **PHASE 4: EDGE REFINEMENT (Month 2+)**

### Monthly Retrospective

After 30 days of trading theo's strategy, analyze:

```
MONTH 1 RESULTS:

Starting capital: 1 SOL
Ending capital: 1.18 SOL
Total trades: 24
Winning trades: 11 (45.8%)
Losing trades: 13 (54.2%)
Average win: +4.2%
Average loss: -5.1%
Biggest win: +8.7%
Biggest loss: -9.2%

Expected (theo at 55%): 1.0 × 1.48 = 1.48 SOL
Actual (you at 45%): 1.18 SOL
Difference: -20% underperformance

Root causes:
├── Slower execution (30s vs 7s) → missed early exits
├── Signal timing (you entered later than theo)
├── Slippage (you got worse fills = -0.5-1% per trade)
└── Psychology (took loss too late, rode win too long)

Adjustments for Month 2:
1. Try 60-second exits instead of 30s (let winners run longer)
2. Use Photon DEX (reduce slippage by 0.3%)
3. Set hard stop-loss (-6%) to prevent catastrophic losses
4. Enter ONLY when you see theo entering (reduce false positives)
```

### Create a Learning Page

`Theo_Strategy_Journey.md`

markdown

```markdown
# Learning theo's Edge: Month 1 Retrospective

## Edge Identified
theo is a momentum scalper who:
1. Finds young tokens (5-15 min old)
2. Waits for volume/whale signal
3. Enters 2% of capital
4. Exits in 7 seconds (hard stop)
5. Captures 4-5% gains, cuts 5-6% losses
6. Achieves 55% win rate on this system

## Edge Replication Attempt
Adapted for human speed:
1. Find tokens on Birdeye trending
2. Wait for volume confirmation (5-min chart)
3. Enter 2% of capital
4. Exit at 60 seconds OR -6% stop loss
5. Aimed for 45%+ win rate

## Month 1 Results
- Win rate: 45.8% ✅ (close to target)
- Returns: +18% ✅ (profitable)
- Slippage: -0.8% ⚠️ (higher than expected)
- Accuracy: Improving (day 30 vs day 1 = +200%)

## Adjustments for Month 2
1. Try 90-second holds (winners run longer)
2. Photon DEX only (reduce slippage)
3. -6% hard stop (prevent -10% losses)
4. Entry only when >3 signals aligned

## Core Insight
theo's edge isn't magic. It's:
- Speed (you can't match, but acceptable)
- Discipline (you CAN match this)
- Signal accuracy (you can improve this with data)
- Risk management (you can copy this exactly)

## Can You Exceed theo's Returns?
Month 1: NO (18% vs theo's 48%)
Month 3: MAYBE (+30-40% if discipline holds)
Month 6: POSSIBLY (+50% if you add your own signals)

The path to exceeding theo is ADDING to his system, not replacing it.
```

---

## **THE COMPLETE LEARNING LOOP**

```
MONTH 1: STUDY
├── Analyze 30 of theo's trades
├── Identify: entry, sizing, exit patterns
├── Understand: WHY each decision
└── Document: Edge Deconstruction.md

MONTH 2: REPLICATE
├── Trade theo's strategy (but at your speed)
├── Track results vs expected
├── Identify: What's working, what's not
└── Document: Strategy Replication Results.md

MONTH 3: OPTIMIZE
├── Adjust timing, signals, sizing
├── Test: Do changes improve win rate?
├── Expand: Add radiance's strategy
└── Document: Hybrid Strategy.md

MONTH 4+: INNOVATE
├── Combine theo + radiance strategies
├── Add your own signals (sentiment, macro, etc.)
├── Build: Custom system
└── Document: [Your Name]'s Trading System.md
```

---

## **TOOLS FOR EDGE EXTRACTION**

### Phase 1: Trade Collection

- Solscan.io (free)
- DexScreener (free)
- Google Sheets (free)
- Obsidian (free)

### Phase 2: Pattern Recognition

- Spreadsheet formulas (calculate win%, avg size, etc.)
- Chart analysis (Birdeye, TradingView)
- Twitter search
- Manual note-taking

### Phase 3: Edge Replication

- Birdeye (free)
- DexScreener (free)
- Backpack/Phantom wallet (free)
- Raydium DEX (free)
- Photon (optional, $0-5/tx)

### Phase 4: Learning & Refinement

- Obsidian (document learning)
- Spreadsheet (track results)
- Solscan (monitor performance)
- Wiki updates (share insights)

---

## **WHAT YOU'LL LEARN BY MONTH 3**

### Understanding

- ✅ Why theo enters specific tokens
- ✅ How theo times entries (volume + whale signals)
- ✅ How theo manages risk (2% per trade)
- ✅ Why theo exits in 7 seconds
- ✅ How theo achieves 55% win rate

### Ability

- ✅ Spot momentum trades independently
- ✅ Size positions correctly
- ✅ Cut losses with discipline
- ✅ Let winners run appropriately
- ✅ Achieve 45-50% win rate (human-speed)

### Intuition

- ✅ "This token is about to pump" (pre-entry)
- ✅ "Now is the time to exit" (exit timing)
- ✅ "This signal is fake" (false positive detection)
- ✅ "I should sit this one out" (patience)

---

## **THE UNFAIR ADVANTAGE: DOCUMENTED LEARNING**

Most traders who try to learn from theo fail because:

- ❌ They don't document their learning
- ❌ They don't systematize what they find
- ❌ They trade emotionally instead of mechanically
- ❌ They don't update their wiki with findings

**You have your wiki.**

Every insight → `Trade_Deconstruction.md`
Every loss → Added to `Loss_Pattern_Analysis.md`
Every win → Added to `Win_Signal_Library.md`

By month 3, you'll have **the most detailed written record of how to trade like theo**.

No other trader has that. That's your edge.

---

## **SUCCESS METRICS: Month 1, 3, 6**

|Metric|Month 1 Target|Month 3 Target|Month 6 Target|
|---|---|---|---|
|Win Rate|45%+|50%+|55%+|
|Monthly Return|+15%|+25%|+40%|
|Avg Trade Size|2%|2.5%|3%|
|Biggest Loss|-9%|-8%|-6%|
|Avg Hold Time|60s|90s|120s|
|Documented Insights|50|200|500|

---

## **The Real Challenge**

Not learning theo's edge. That's months 1-2.

**The real challenge:** Building on theo's edge in month 4+.

Once you've mastered momentum scalping, you can:

- Add macro signals (Bitcoin price, Fed news)
- Add sentiment analysis (Twitter momentum scores)
- Add token fundamentals (creator reputation, liquidity lock)
- Combine with radiance's strategy (different tokens, different timing)

**That's where 1 SOL becomes 10 SOL.**

---

## **Your Wiki Grows With Every Trade**

This entire learning journey becomes 5-10 new wiki pages:

1. `Theo_Trade_Deconstruction.md` (Phase 1)
2. `Momentum_Scalping_Framework.md` (Phase 2)
3. `Trade_Replication_Results.md` (Phase 3)
4. `Entry_Signal_Library.md` (ongoing)
5. `Exit_Strategy_Playbook.md` (ongoing)
6. `Loss_Prevention_Rules.md` (ongoing)
7. `My_Adaptation_of_Theo_Strategy.md` (Phase 4)

By month 3, your wiki is a **complete trading manual** based on real data, real analysis, real results.

No course, no book, no mentor has that specificity.

---

## **Start Here (Tomorrow)**

1. ✅ Get theo's wallet address
2. ✅ Go to Solscan
3. ✅ Find 5 of theo's recent trades
4. ✅ Document each one (entry, exit, PnL)
5. ✅ Analyze the pattern (volume? price movement? timing?)
6. ✅ Create `Theo_Trade_Deconstruction_Start.md` in your wiki

That's it. That's the first step. One hour of work.

By tomorrow night, you'll know MORE about theo's edge than 99% of copy traders.

By week 2, you'll be ready to trade theo's strategy independently.

By month 3, you'll BE theo (or better).

---

## Related

- [[frameworks/farmer-detection]] — How to spot real traders vs farming exploits
- [[traders/theo]] — Theo's profile and trading record
- [[playbooks/theo-style]] — Theo's operational playbook for daily trading
- [[patterns/winner-checklist]] — Validation framework for token entry decisions
- [[playbooks/narrative-trade]] — Complementary approach (narrative vs technicals)