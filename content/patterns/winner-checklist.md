---
title: "Winner Checklist — Go / No-Go Decision Framework"
name: Winner Checklist — Go / No-Go Decision Framework
type: pattern
tags: [pattern, signal]
---

# Winner Checklist — Go / No-Go Decision Framework

> **Data confidence: MEDIUM** — Section 1 (narrative gate) validated against 1 winner + 16 hard failures. 100% filter rate on failures at 4+/6 threshold. BC and Migration sections still need loser-side on-chain validation.

The master checklist for evaluating whether a coin is worth entering. Covers narrative, bonding curve signals, and post-migration volume.

---

## When to Use This

| Situation | Which section |
|-----------|--------------|
| Saw a narrative trigger (tweet, news) | Section 1 first |
| Token just launched, BC active | Section 1 + 2 |
| Token just migrated to pumpAMM | Section 1 + 2 + 3 |
| Evaluating a trader's pick after the fact | Section 2 + 3 |

---

## Section 1 — Narrative Check

Score 1 point per item. **Score 4+/6 → proceed to Section 2.**

```
[ ] Source is a verifiable public figure (not anonymous)
[ ] Source has 1M+ followers OR is a known industry CEO/founder
[ ] Token name = exact word or phrase used by the source
[ ] The underlying event is organic (not manufactured for the coin)
[ ] The thesis can be stated in 1 sentence without crypto jargon
[ ] There is lore / meaning / cultural resonance to the name

SCORE: ___ / 6

< 4: Stop. Narrative too weak.
4–5: Proceed with caution.
6:   Maximum conviction narrative.
```

---

## Section 2 — Bonding Curve Signals

Check these if BC is still active. **All 3 required to proceed.**

```
[ ] BC fill time is < 30 minutes (or < 50% filled at < 10 min)
    → How to check: Solscan token page, launch tx timestamp vs now
    → embers baseline: 23 minutes

[ ] Dev bought at launch (visible in launch tx)
    → How to check: Solscan launch tx — first buyer = dev wallet
    → embers baseline: $856 (10 SOL)

[ ] Multiple sniper wallets visible in first Solscan transactions
    → How to check: First 10 txs on BC pool, count unique wallets
    → embers baseline: 16 unique wallets in first 2 seconds

SCORE: ___ / 3

< 2: Weak BC signal. Very risky.
2:   Acceptable.
3:   Strong BC signal.
```

---

## Section 3 — Post-Migration Volume (at t=30s)

Check these exactly at t=30s post-migration. **Enter at t=45s if 4+/5 pass.**

```
[ ] Total volume > $300 in first 30s
    → embers: $752 ✅

[ ] At least 1 buy > $100 in first 30s
    → embers: $169 whale buy at t+8s ✅

[ ] Same wallet bought 3+ times (bot accumulation)
    → embers: CYZcucbb — 8 micro-buys ✅

[ ] Buy transaction count > sell transaction count
    → embers: 12 buys / 8 sells ✅

[ ] Net sell pressure < -$500
    → embers: -$380 ✅

SCORE: ___ / 5

< 3: Do not enter. Migration too sell-heavy.
3:   Borderline — small position only.
4–5: Enter at t=45s.
```

---

## Hard No-Entry Rules (Any One Fails = Skip)

Regardless of scores above, do NOT enter if:

- ❌ Zero buys > $50 in first 30s post-migration — no smart money at all
- ❌ Only 1–2 unique buy wallets in first 30s — manipulation risk
- ❌ Net sell pressure > -$1,000 in first 30s — coordinated dump, not BC exit
- ❌ The token's BC fill time was > 60 minutes — too slow, no momentum
- ❌ BC already > 50% filled when you first see the narrative — missed the best entry
- ❌ The "source" tweet is more than 2 hours old — narrative already stale
- ❌ Token name contains "scam", "rug", "ponzi", "exploit", or "drain" — bot trap, zero post-migration demand. Validated: 5/5 hard failures, 0% win rate. *(Added Apr 28 — [[patterns/hard-failure-postmortem-apr2026]])*
- ❌ Same name or close variant already migrated this session — original captures the meta, every copy fails. Validated: Dog In Vest vs Vesting ($307K). *(Added Apr 28 — [[patterns/hard-failure-postmortem-apr2026]])*

---

## Entry Timing Decision

```
Narrative score 4+/6 → BC score 2+/3 → Migration score 4+/5
                                              ↓
                                     ENTER AT t=45s post-migration
                                     Position: 3–7% of capital
                                     Stop: -15%
                                     Target: +5% (50%), +10% (50%)
```

For position sizing rules, see [[playbooks/theo-style]].
For migration-specific entry playbook, see [[playbooks/migration-alert]].

---

## Updating This Checklist

Every new coin studied should result in updating at least one threshold:

| When to update | What to update |
|----------------|---------------|
| New winner studied | Confirm thresholds still pass |
| First loser studied | Identify which signal was absent — tighten that threshold |
| 10+ cases | Calculate hit rate per signal, reprioritize weights |

---

## Score History

| Coin | Narrative | BC | Migration | Outcome |
|------|-----------|----|-----------|---------|
| embers | 6/6 | 3/3 | 5/5 | ✅ Winner |
| Scams Pump the Hardest ×2 | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| Scams And Profit 500 | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| Scamcoin | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| Sam Snakeman | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| OMNITRADING | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| WeLoveDicks | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| Legit Coin | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| For Profit Coin | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| Unfazed | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| up | 0/6 | —/3 | —/5 | ❌ Hard Failure |
| Dog In Vest | 2/6 | —/3 | —/5 | ❌ Hard Failure (copy) |
| OpenLie | 2/6 | —/3 | —/5 | ❌ Hard Failure |
| Helping Hand | 1/6 | —/3 | —/5 | ❌ Hard Failure |
| AmericanReserveModernizationAct | 1/6 | —/3 | —/5 | ❌ Hard Failure |
| Israeli shekel | 2/6 | —/3 | —/5 | ❌ Hard Failure |

*BC and Migration sections marked —/3 and —/5: Section 1 terminates evaluation, these tokens never reached the on-chain check.*

→ Full failure analysis: [[patterns/hard-failure-postmortem-apr2026]]

---

## Related Pages

- [[coins/coin-index]]
- [[patterns/narrative-triggers]]
- [[patterns/migration-signals]]
- [[patterns/volume-fingerprints]]
- [[playbooks/migration-alert]]
- [[playbooks/narrative-trade]]
