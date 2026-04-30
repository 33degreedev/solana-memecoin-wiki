---
title: "Vamping Framework"
name: Vamping Framework
type: pattern
tags: [pattern, signal]
---

# Vamping Framework

> **Data confidence: MEDIUM** — Based on 1 confirmed vamping case (AIB). Framework logic is solid; individual signal weights need more cases to validate.

## What Is Vamping?

**Vamping** is when traders who missed the original coin — or disagree with its platform/format, picture, name/ticker, etc. — launch competing coins with the same name and narrative, attempting to drain momentum and capital from the original by claiming their version is more legitimate.

The term comes from "vampire" — one version tries to drain the life out of the other.

---

## How Vamping Works

```
STEP 1: Narrative trigger fires (tweet, news, event)
         ↓
STEP 2: Original coin launches (first mover, usually pump.fun)
         ↓
STEP 3: Dissenters emerge:
        "This should be on [other platform]"
        "That one's not the real OG"
        "Better ticker exists: [X]"
         ↓
STEP 4: Competing coins launch with same name + a legitimacy argument
         ↓
STEP 5: Capital splits between coins
         ↓
STEP 6: One coin wins (narrative fit), others die
```

**Result:** The trader who correctly identified which coin would win the legitimacy battle profits. Everyone else either exits at breakeven or holds a dead coin.

---

## The Cost of Vamping: What Concentrated Capital Would Have Done

When capital splits across competing coins, each coin is starved of the momentum it would have had alone. The AIB case shows exactly how much value vamping destroys.

### AIB Volume Split (Actual)

| Coin | Volume | ATH MC |
|------|--------|--------|
| pump.fun AIB (Original) | $1.7M | $251K |
| Bonk AIB (Vamp 1) | $2.8M | $658K |
| OG Bonk AIB (Vamp 2) | $593K | ~$237K |
| **Total** | **$5.093M** | — |

### If All Capital Had Gone to One Coin

Total volume across all three coins: **$5.093M**

Bonk AIB achieved $658K ATH on $2.8M of that volume. If all $5.093M had concentrated into Bonk AIB:

```
$658K × (5.093 / 2.8) ≈ $1.2M projected ATH (linear estimate)

Realistic range: $1.5M–$2M+
  — FOMO compounds non-linearly as price rises
  — Momentum attracts more buyers at higher prices
  — Single narrative = press coverage, CT virality, more entry points
```

**Bonk AIB's actual ATH: $658K. Potential ATH with no vamping: ~$1.5M–$2M.**

The capital split cost the winning coin roughly **$850K–$1.35M in unrealized ATH.**

### Why This Matters for Trading

- Vamping doesn't just create noise — it actively suppresses the winner's ceiling
- A 5/6 narrative that runs clean to one coin is worth more than a 6/6 narrative that vamps
- The same $5M of buying pressure produces a 3× higher ATH when it's not split
- This is why picking the right coin in a vamping scenario is not just about avoiding losses — it's about capturing the return that concentrated capital generates

**Lesson:** In a single-coin narrative, the winner gets all the momentum. In a vamping scenario, even the winning coin underperforms its potential. The cost of being in the wrong coin is total. The cost of vamping itself is ~2–3× of the winner's actual ATH.

---

## Vamping Legitimacy Arguments (Ranked by Strength)

Not all legitimacy arguments are equal. Here's how to rank them:

| Rank | Argument Type | Example | Strength |
|------|--------------|---------|----------|
| 1 | Platform aligns with narrative subject | "Trump is Bonk → AIB should be Bonk" | 🟢 STRONG |
| 2 | Official/verified endorsement | "The real account tweeted our address" | 🟢 STRONG |
| 3 | Higher-quality metrics at launch | "Ours has 0% dev tokens, 100% LP burned" | 🟡 MEDIUM |
| 4 | Earlier launch timestamp | "We were first by 10 minutes" | 🟡 MEDIUM (weak) |
| 5 | "We're the OG" with no backing | "We're the original" | 🔴 WEAK |
| 6 | Better ticker | "AIB > AMERICA" | 🔴 WEAK |

**The AIB case:** Bonk AIB's argument ("Trump = Bonk platform") was Rank 1. pump.fun AIB's only counter was Rank 4 (first mover). Result: Bonk AIB won comprehensively.

---

## Detecting a Vamping Scenario

**Early signals (within 5–10 minutes of narrative trigger):**

```
[ ] 2+ tokens with same name visible on Axiom/DexScreener search
[ ] Competing Twitter/CT accounts promoting different versions
[ ] Active debate on CT about "which one is the real X"
[ ] Platform-specific argument emerging ("should be on Y, not Z")
[ ] Volume splitting — no single coin has > 70% of total AIB volume
```

**If 2+ of these are true → VAMPING IS OCCURRING. Do not enter blindly.**

---

## Decision Framework: Which Coin to Buy in a Vamp

### Step 1: Map the coins

List every coin with the same name. For each, note:
- Platform
- Legitimacy argument being made
- Source/promoter (follower count)
- Volume % share of total
- BC fill speed (if still active)

### Step 2: Score legitimacy arguments

Use the ranking table above. Assign scores 1–6 (1 = strongest).

### Step 3: Check source credibility

| Source | Signal |
|--------|--------|
| Same high-credibility account linked to multiple coins | Neutral — doesn't differentiate |
| High-credibility source links specifically to one coin | 🟢 Strong signal for that coin |
| Low-follower account promoting a coin as "OG" | 🔴 Red flag — ignore |

### Step 4: Check volume share

| Volume share | Interpretation |
|-------------|---------------|
| One coin > 70% of total volume | Clear winner emerging — buy that one |
| 50/50 split | Vamp undecided — wait or skip |
| Three-way split with no dominant coin | Too uncertain — skip all |

### Step 5: Decide

```
SCORE 1 legitimacy + HIGH volume share + STRONG source = ENTER
SCORE 4-6 legitimacy + LOW volume share + WEAK source = SKIP
Unclear winner = WAIT until volume concentrates
Already in losing coin = EXIT, evaluate switching
```

---

## The Four Vamping Outcomes

### Outcome A: Original Wins
Original coin maintains dominance despite vamp. Vamp fails to gain traction.
**When:** Original has strong platform alignment, no compelling counter-argument.
**What to do:** Stay in original (or enter original if you see vamp failing early).

### Outcome B: Vamp Wins (AIB case)
Vamp coin overtakes original via stronger legitimacy argument. Original collapses.
**When:** Vamp has platform/endorsement advantage that resonates with the community.
**What to do:** Exit original quickly. Enter vamp during its BC phase if possible.

### Outcome C: Both Die
Narrative attention splits too much across coins. Neither reaches critical mass. Both dump.
**When:** Multiple low-quality vamps dilute the narrative, or narrative was weak to begin with.
**What to do:** Exit all positions early. If narrative score was < 4/6, this was predictable.

### Outcome D: New Coin Emerges (Third-Party Win)
A completely different version of the coin — better ticker, better platform — launches after the original and both vamps, and wins by being "the clean start."
**When:** First 3 coins are all tainted (dev tokens, bad tokenomics) — community restarts.
**What to do:** Extremely hard to predict. Only enter if you see strong community consensus forming around the new version.

---

## Vamping vs Single-Coin Narrative: Key Differences

| Factor | Single Coin (embers) | Vamping Scenario (AIB) |
|--------|---------------------|----------------------|
| Decision complexity | Low — one coin | High — must pick winner |
| Entry timing | Straightforward | Wait until vamp direction clear |
| Risk of being in wrong coin | N/A | HIGH — wrong coin = total loss |
| Time to resolve | Instant | 10–30 minutes for winner to emerge |
| Narrative quality needed | 4+/6 | 5+/6 (strong narratives attract more vamps) |

**Strong narratives attract more vamps.** The better the catalyst, the more competing coins will appear. High narrative quality → higher vamping probability.

---

## How to Adjust the [[patterns/winner-checklist]] for Vamping

When a vamping scenario is detected, add these checks **before** entering any coin:

```
VAMPING CHECK (run before Section 3 of Winner Checklist):

[ ] Have I identified ALL coins with this name?
[ ] Have I scored each legitimacy argument (see table above)?
[ ] Is one coin clearly winning on volume share (> 60%)?
[ ] Does the winning-legitimacy coin have a credible source (> 500K followers)?
[ ] Am I NOT currently holding the losing coin?

If any ❌ → Wait 5–10 more minutes. Winner not yet clear.
```

---

## Case Studies

### AIB — America Is Back (Apr 23, 2026) — Outcome B: Vamp Wins

| Coin | Platform | Legitimacy | Volume | Outcome |
|------|---------|-----------|--------|---------|
| EjP...pump (Original) | pump.fun | First mover | $1.7M | ❌ Dead ($14K) |
| Ggi...bonk (Vamp 1) | Bonk | Trump = Bonk alignment | $2.8M | ✅ Alive ($364K) |
| 7DR...bonk (Vamp 2) | Bonk | "OG" claim | $593K | ❌ Dead ($15K) |

**Winner signal:** Bonk AIB had Rank 1 legitimacy (platform alignment) + highest volume share (52% of total) within 30 minutes.

Full analysis: [[coins/aib-america-is-back]]

---

## Quick Reference: What To Do When You See a Vamp

```
DETECT: 2+ same-name coins visible → PAUSE entry

MAP: List all coins, their platform, and their argument

SCORE: Which has the strongest legitimacy claim?
  Platform alignment = strongest
  Official endorsement = strongest
  "OG" claim alone = ignore

VOLUME: Which has > 60% of total volume?

DECIDE:
  Clear winner on both legitimacy AND volume → Enter that coin
  Split or unclear → Wait 10 min and check again
  Already in the wrong coin → EXIT, switch or stay out

EXIT: Apply standard [[playbooks/theo-style]] exit rules
```

---

## Related Pages

- [[coins/aib-america-is-back]]
- [[patterns/narrative-triggers]]
- [[patterns/winner-checklist]]
- [[playbooks/narrative-trade]]
- [[coins/coin-index]]
