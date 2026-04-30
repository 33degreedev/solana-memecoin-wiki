---
title: "Migration Alert Playbook — How to Trade pumpAMM Graduations"
name: Migration Alert Playbook — How to Trade pumpAMM Graduations
type: playbook
tags: [playbook, strategy]
---

# Migration Alert Playbook — How to Trade pumpAMM Graduations

> **Based on:** [[coins/embers]] (single case). Thresholds are starting hypotheses, not validated rules.

A step-by-step guide for monitoring pump.fun migrations, evaluating them in real time, and entering at the optimal window (t=45s post-migration).

---

## Why Migrations Matter

When a pump.fun bonding curve fills (~$69K), the token graduates to pumpAMM. This creates a predictable pattern:
1. BC holders dump immediately into new liquidity (sell pressure front-loaded)
2. Smart money/whales absorb the dump (confirmation signal)
3. Buyers pile in as sellers exhaust (entry window opens)

The t=30–60s window is the sweet spot: enough data to confirm absorption, early enough to capture momentum.

---

## Setup (One Time)

- [ ] Bookmark Solscan, DexScreener, GeckoTerminal
- [ ] Find a migration alert source (options below)
- [ ] Practice identifying pumpAMM pool addresses vs BC addresses on Solscan
- [ ] Have wallet ready with SOL for entries

**Migration detection sources:**
| Source | Method | Speed |
|--------|--------|-------|
| DexScreener | Filter new Solana pairs, sort by newest | ~30s lag |
| Birdeye | Trending new tokens, check pool type | ~60s lag |
| Solscan | Watch pumpAMM program for new pool creation | Real-time (advanced) |
| Twitter/X | Follow accounts that announce migrations | Variable |
| Axiom | Migration dashboard (requires account) | Near real-time |

---

## Real-Time Decision Protocol

### At Migration Detection (t=0)

**Do:** Note the exact timestamp. Start a 30-second mental clock.
**Check:** Is there a narrative? → Score Section 1 of [[patterns/winner-checklist]]
**Don't enter yet.** First 30 seconds are for observation only.

---

### At t=30s

Run the post-migration volume check:

```
Open Solscan → pumpAMM pool → DeFi Activities → last 30s

Count:
  Buy txs: ___    Sell txs: ___    → Buys > Sells? ✅/❌
  Buy vol: $___   Sell vol: $___   → Total vol > $300? ✅/❌
  Largest buy: $___               → > $100? ✅/❌
  Same wallet bought 3+? ___      → Yes? ✅/❌
  Net flow: $___                  → > -$500? ✅/❌

PASS 4+/5 → SET ENTRY ORDER FOR t=45s
PASS < 4  → WATCH. Do not enter.
```

---

### At t=45s

**If 4+/5 signals passed at t=30s:**
- Enter 5% of capital (see [[playbooks/theo-style]] position sizing)
- Set 60-second timer immediately
- Apply theo exit rules: +5% sell 50%, +10% sell all, -15% cut, 60s hard stop

**If signals didn't pass:**
- Continue watching. Check again at t=60s and t=90s.
- If no flip by t=90s (buy pressure still negative), skip this migration.

---

### At t=60–120s

If you entered at t=45s:
- Follow exit rules strictly
- The 60–120s bucket should be net positive on a winner (embers was +$311)
- If net is negative by t=120s, execute time exit regardless

If you didn't enter:
- Check if the 30–60s flip happened (buy pressure reversed)
- Late entry at t=90s is lower conviction — reduce position to 3%

---

## Reading the Sell Pressure at Migration

**Expected:** Large sell at t=5s. BC holders have been sitting for 20–40 minutes and dump immediately into new AMM liquidity. This is NOT a red flag.

**The question is:** Who absorbs the dump?

| Absorber type | Signal | What to expect next |
|--------------|--------|---------------------|
| Whale ($100+ single buy) | 🟢 Smart money | Strong continuation |
| Multiple small buys ($10–50 each) | 🟡 Retail | Moderate continuation |
| Bot micro-buys (8× $0.08) | 🟢 Programmatic | Signals passed an automated filter |
| No buyers in first 30s | 🔴 No demand | Skip this migration |

---

## The Embers Pattern (Reference)

```
t+0s:  $4.26 sniper buy (first)
t+5s:  $270 BC holder dump
t+8s:  $169 whale buy (absorption signal ✅)
t+13–29s: Bot CYZcucbb × 8 micro-buys (programmatic signal ✅)
t+28s: Whale flips at +29% in 20 seconds
t+30s: CHECK → 12 buys / 8 sells, $752 total, $169 largest buy ✅
t+45s: ENTER (all signals passed)
t+30–60s: 11 buys / 1 sell, +$257 net (flip confirmed ✅)
t+60–120s: +$311 net (momentum building ✅)
```

---

## What This Looks Like on a Loser (Hypothesized)

Not yet confirmed. Expected pattern:
- Large sell(s) at t=5s
- No significant buys absorbing the dump
- Volume < $100 in first 30s
- 0–1 unique buy wallets
- Net flow -$800 or worse at t=30s
- Skip → price likely dumps further post-migration

---

## Building the Pattern Database

After each migration you evaluate (whether you enter or not), log:

```
Date:
Token:
Narrative (if any):
BC fill time:
t=30s signals: vol=$__ buys=__ sells=__ largest_buy=$__ net=$__
Decision: ENTER / SKIP
Outcome (if entered): +__% / -__%
```

Add results to [[coins/coin-index]] and update thresholds in [[patterns/winner-checklist]].

---

## Related Pages

- [[patterns/migration-signals]]
- [[patterns/winner-checklist]]
- [[patterns/volume-fingerprints]]
- [[coins/embers]]
- [[playbooks/theo-style]]
- [[playbooks/narrative-trade]]
