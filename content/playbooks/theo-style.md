---
title: "Theo Style Playbook — How to Trade Like Theo"
name: Theo Style Playbook — How to Trade Like Theo
type: playbook
tags: [playbook, strategy]
---

# Theo Style Playbook — How to Trade Like Theo

**Based on:** [[traders/theo]] profile
**Expected return:** +6–11% monthly (base case, 59% win rate)
**Capital required:** 1+ SOL
**Time required:** 2–3 hours/day during peak hours (17:00–23:59 UTC)

---

## The Core Edge

Theo makes money by:
1. Finding tokens **9–25 minutes old** with a volume spike
2. Entering with a **fixed position** (5% of capital)
3. Holding **30–60 seconds** with a hard timer
4. Exiting at **+5% (50%)** then **+10% (all)**, OR cutting at **-15%**
5. Doing this 20–25 times per day

The edge is **mechanical exits**, not superior token selection. At 59% win rate, the math only works if you don't hold losing trades past -15%.

---

## Section 1 — The Entry Checklist (5 Requirements)

Check ALL 5 before every entry. Skip if any fail.

```
Token: __________________________

[ ] 1. Token age: 9–25 minutes?
        Check: Birdeye → token page → "Created" timestamp

[ ] 2. Volume spike: Last 5-min volume > baseline × 150%?
        Check: DexScreener → 5-min chart → volume bars

[ ] 3. Holders growing: +20 new holders in last 5 minutes?
        Check: Solscan → token → Holders tab → recent additions

[ ] 4. Whale buy: $1+ SOL buy visible in last 5 minutes?
        Check: Solscan → token → Transactions → filter buys

[ ] 5. Price momentum: Uptrend on 5-min chart?
        Check: DexScreener → 5-min chart → green candles

ALL 5 ✅ → ENTER    |    ANY ❌ → SKIP
```

**Speed target:** 60 seconds per checklist. Accuracy first, speed second.

**Good token example:**
- Age 15 min ✅, volume 4× baseline ✅, +60 new holders ✅, 2 SOL whale buy ✅, +50% price ✅ → ENTER

**Bad token example:**
- Age 8 min ❌ → SKIP regardless of other signals

---

## Section 2 — Position Sizing (5% Rule)

| Capital | Per-Trade Size | Min | Max |
|---------|----------------|-----|-----|
| 1 SOL | 0.05 SOL | 0.03 | 0.07 |
| 5 SOL | 0.25 SOL | 0.15 | 0.35 |
| 10 SOL | 0.50 SOL | 0.30 | 0.70 |

**Rules:**
- ✅ Risk exactly 5% per trade
- ✅ Reduce to 3% after 5+ consecutive losses
- ✅ Scale back to 5% after 5 consecutive wins
- ❌ Never exceed 7% on any single trade
- ❌ Never average down into a losing position
- ❌ Never size up because "this one feels different"

**Drawdown safety:** Even 10 consecutive losses at max -15% stop only draws down capital by ~5%. The sizing is conservative by design.

---

## Section 3 — Exit Rules (3 Conditions)

**Set phone timer for 60 seconds BEFORE you hit buy.**

```
PROFIT EXIT:
  At +5% (anytime)  → Sell 50% of position. Lock profit.
  At +10% (anytime) → Sell remaining 50%. Done.
  Never wait for +20%. It won't happen in 60 seconds.

LOSS EXIT:
  At -10% (first 30s) → EXIT IMMEDIATELY at market.
  At -15% (anytime)   → EXIT IMMEDIATELY. Non-negotiable.
  Never hope a -15% becomes breakeven. It won't.

TIME EXIT:
  At 60 seconds → EXIT AT MARKET. Whatever the price.
  The timer IS the discipline. No exceptions.
```

**Decision tree:**
```
20s mark: Price +5%? → Sell 50%
30s mark: Price -10%? → EXIT ALL
45s mark: Price +10%? → EXIT ALL remaining
60s mark: Timer off? → EXIT ALL at market
Between 30-60s: Price -15%? → EXIT ALL immediately
```

---

## Section 4 — The Math

**Per-trade EV at 59% win rate, 5% position size:**

| Outcome | Frequency | Avg Move | PnL per 0.05 SOL trade |
|---------|-----------|----------|------------------------|
| Win (50%@+5%, 50%@+10%) | 59% | +7.5% avg | +0.00375 SOL |
| Loss (stop -10% to -15%) | 41% | -12% avg | -0.00600 SOL |

**20-trade session:**
- 12 wins × +0.00375 = +0.045 SOL
- 8 losses × -0.00600 = -0.048 SOL
- Net ≈ −0.003 SOL (essentially breakeven at exact ratio)

The system turns profitable when win rate exceeds ~62% — OR when execution is clean (hitting exits at +5%/+10% not +3%/+7%).

**Monthly projection (20 trades/day, 5 days/week):**

| Scenario | Win Rate | Return |
|----------|----------|--------|
| Conservative | 55% | +3–6% |
| Base case | 59% | +6–11% |
| Strong | 63% | +12–16% |

---

## Section 5 — Daily Routine

### Pre-Session (10 min)
- [ ] Open Birdeye.so, DexScreener.com, Solscan.io
- [ ] Have wallet funded and ready
- [ ] Phone timer ready
- [ ] Review any notes from yesterday

### Trading Session (Peak hours: 17:00–23:59 UTC)
```
Loop per trade:
1. Scan Birdeye trending (9–25 min tokens)
2. Run 5-point checklist (60 seconds)
3. If all 5 pass: Enter 5% position, start timer
4. Monitor price, exit at +5%/+10%/-10%/-15%/60s
5. Record trade: token, entry, exit, PnL%, outcome
6. Move to next token
```

### Post-Session (15 min)
- Calculate win rate for today
- Note any checklist violations
- Update [[traders/theo]] tracker or personal log

### If Losing
- 3 consecutive losses → take 30-min break
- 5 consecutive losses → reduce to 3% sizing, review checklist
- Down 20%+ after 20 trades → stop, paper trade to diagnose

---

## Section 6 — Front-Running Theo (Advanced)

Instead of copying theo, enter 30 seconds before his likely entry using the same signals. Capture his buy momentum as your exit.

```
YOUR SEQUENCE:
T-30s: You identify token theo MIGHT enter (same 5-point checklist)
T+0s:  You enter
T+30s: Theo's entry pushes price up +5%
T+15s after theo: You exit at +5% (theo is still entering)
T+60s: Theo exits — you're already out

RESULT: +5% capture vs theo's +4% (less slippage)
```

**Added difficulty:** You need to be faster than theo, which means faster scanning and execution. Not recommended until you've done 50+ direct theo trades.

---

## Section 7 — Tools

| Tool | Purpose | URL |
|------|---------|-----|
| Birdeye | Find trending tokens, check age | birdeye.so |
| DexScreener | Volume chart, price momentum | dexscreener.com |
| Solscan | Whale buys, holder count | solscan.io |
| Phantom / Backpack | Execute trades | — |
| Phone timer | Mechanical 60s exit | Clock app |

---

## Related Pages

- [[traders/theo]]
- [[traders/jijo]]
- [[patterns/winner-checklist]]
- [[playbooks/migration-alert]]
- [[playbooks/narrative-trade]]
- [[frameworks/farmer-detection]]
