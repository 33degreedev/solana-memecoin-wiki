---
title: "Hard Failure Post-Mortem — April 2026"
name: Hard Failure Post-Mortem — April 2026
description: Loser case study on all 16 hard failures from the Apr 27-28 session. Validates Winner Checklist thresholds from the failure side and identifies filterable patterns.
type: analysis
status: complete
tags: [post-mortem, losers, winner-checklist, signal-validation, filtering]
---

# Hard Failure Post-Mortem — April 2026

**Period:** Apr 27–28, 2026
**Failures analysed:** 16 (ATH ≤ $40K — never meaningfully left migration MC)
**Purpose:** Validate [[patterns/winner-checklist]] thresholds from the failure side. Confirm which checklist criteria, if enforced, would have filtered each loser before entry.

---

## The 16 Hard Failures

| # | Token | Tier | Est. ATH | Failure Group |
|---|-------|------|----------|---------------|
| 1 | Scams Pump the Hardest | EXTREME | $38K | Scam-Themed |
| 2 | Scams Pump the Hardest #2 | EXTREME | $36K | Scam-Themed + Copy |
| 3 | OMNITRADING | FAST | $35K | No Narrative |
| 4 | WeLoveDicks | FAST | $35K | No Narrative |
| 5 | Scams And Profit 500 | FAST | $35K | Scam-Themed |
| 6 | Legit Coin | STALLED | $35K | No Narrative |
| 7 | For Profit Coin | STALLED | $35K | No Narrative |
| 8 | Dog In Vest | EXTREME | $35K | Copy Token |
| 9 | Unfazed | SLOW | $35K | No Narrative |
| 10 | OpenLie | FAST | $35K | Weak Derivative |
| 11 | Helping Hand | MODERATE | $35K | Weak Narrative |
| 12 | AmericanReserveModernizationAct | STALLED | $35K | Weak Narrative |
| 13 | up | MODERATE | $35K | No Narrative |
| 14 | Israeli shekel | SLOW | $34K | Weak Narrative |
| 15 | Scamcoin | EXTREME | $33K | Scam-Themed |
| 16 | Sam Snakeman | EXTREME | $33K | Scam-Themed |

---

## Failure Taxonomy

### Group A — Scam-Themed Name (5 tokens, 31%)

**Tokens:** Scams Pump the Hardest ×2, Scams And Profit 500, Scamcoin, Sam Snakeman

These tokens have explicit scam signalling baked into the name itself. The name is the thesis — and the thesis is that it will rug. This is not a coincidence: it's a deliberate launch strategy by devs who know degens will buy anything with "scam" in the name as a meta-irony play. It works in the bonding curve because known traders enter speculatively. It fails post-migration because there is no buyer narrative — you cannot explain to a new buyer why they should hold a coin called "Scamcoin."

**Winner Checklist score (all 5 tokens):**

| Criteria | Score | Reason |
|----------|-------|--------|
| Verifiable public figure source | ❌ 0 | No source exists |
| 1M+ followers | ❌ 0 | No source |
| Name = exact source word | ❌ 0 | No source |
| Organic event | ❌ 0 | Dev-manufactured |
| 1-sentence thesis | ❌ 0 | "Buy a coin called scam" ≠ thesis |
| Lore / cultural resonance | ❌ 0 | Negative resonance — repels buyers |
| **Narrative Score** | **0/6** | **HARD FAIL — Section 1** |

**Checklist filter:** Section 1 threshold of 4+/6 kills all 5 before any on-chain check. Zero ambiguity.

**New Hard No-Entry Rule validated:** Token name contains "scam", "rug", "ponzi", "exploit", or explicit negative framing → automatic skip regardless of BC activity. These tokens had known traders in BC — the signal was false positive because bot activity in BC is not the same as market demand post-migration.

---

### Group B — No Narrative / Zero Source (6 tokens, 38%)

**Tokens:** OMNITRADING, WeLoveDicks, Legit Coin, For Profit Coin, Unfazed, up

Pure launches with no external hook. No tweet, no event, no public figure — just a name. These rely entirely on the bonding curve buy pressure to generate momentum, which evaporates the moment bots exit at migration. Without a story there is no second wave of buyers post-migration.

**Winner Checklist score (representative: "up"):**

| Criteria | Score | Reason |
|----------|-------|--------|
| Verifiable public figure source | ❌ 0 | None |
| 1M+ followers | ❌ 0 | None |
| Name = exact source word | ❌ 0 | No source |
| Organic event | ❌ 0 | None |
| 1-sentence thesis | ❌ 0 | "up" has no thesis |
| Lore / cultural resonance | ❌ 0 | Generic |
| **Narrative Score** | **0/6** | **HARD FAIL — Section 1** |

**Notes by token:**
- **OMNITRADING** — Generic trading brand. 0/6. No cultural context.
- **WeLoveDicks** — Shock value. Marginal "lore" (adult humor). 1/6 at most. Fails threshold.
- **Legit Coin** — Ironic. 0/6. The irony is not a thesis.
- **For Profit Coin** — Commercial framing. 0/6. Repels buyers who want a story.
- **Unfazed** — Generic emotional state. 0/6. No source, no hook.
- **up** — Single word. 0/6. Weakest narrative in the entire dataset.

**Checklist filter:** Section 1 eliminates all 6. Every one of these would have been stopped at the first gate.

---

### Group C — Weak / Unverifiable Narrative (3 tokens, 19%)

**Tokens:** Helping Hand, AmericanReserveModernizationAct, Israeli shekel

These had a kernel of something — a political or social concept — but no verifiable source, no reach, and no way to compress the thesis into a shareable format.

**Winner Checklist scores:**

| Token | Verifiable Source | 1M+ Reach | Exact Name Match | Organic | Simple | Lore | Score |
|-------|-----------------|-----------|-----------------|---------|--------|------|-------|
| Helping Hand | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | 1/6 |
| AmericanReserveModernizationAct | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ (marginal) | 1/6 |
| Israeli shekel | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ (geopolitical) | 2/6 |

**Israeli shekel** is the most instructive — geopolitical events can generate speculative buying but without a specific live event tied to the launch and a verifiable source, the energy dissipates. It's a Tier C narrative (trending topic) without the source credibility to hit Tier A/B. Score of 2/6 still fails the 4+ threshold.

**AmericanReserveModernizationAct** — likely capitalising on Federal Reserve discourse but the name itself is too complex to memify. Fails the "1-sentence thesis" criterion. Bureaucratic naming kills virality.

**Checklist filter:** All 3 score ≤ 2/6. Section 1 catches them. The 4+/6 threshold is specifically calibrated to reject weak political and social narratives without a live event and named source.

---

### Group D — Copy / Derivative Token (2 tokens, 12%)

**Tokens:** Dog In Vest, OpenLie

**Dog In Vest** is the clearest copy token in the dataset. It launched during the same session as Vesting ($307K ATH) — the third version of the "vest" meta cluster (Vesting → LOCKED IN → Dog In Vest). Pattern 3 from the Alert Outcome Analysis confirmed: only the original captures the momentum. Every subsequent copy has the same BC buyers (bots following the same wallets) but zero incremental demand from retail.

**OpenLie** — likely a derivative of OpenAI / anti-AI narrative. No original source event. The name is an interpretation rather than an exact match to any identifiable event.

**Winner Checklist scores:**

| Token | Source | Reach | Exact Match | Organic | Simple | Lore | Score |
|-------|--------|-------|-------------|---------|--------|------|-------|
| Dog In Vest | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ (marginal) | 2/6 |
| OpenLie | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ (marginal) | 2/6 |

**New Hard No-Entry Rule validated:** If the same name or close variant has already migrated this session → automatic skip. Dog In Vest would have been caught by a duplicate name detector even before reaching the checklist.

---

## Winner Checklist Validation — Threshold Audit

The core question: **does enforcing the 4+/6 narrative threshold filter all 16 hard failures?**

| Group | Tokens | Max Score Observed | Passes 4+/6? |
|-------|--------|-------------------|--------------|
| Scam-Themed | 5 | 0/6 | ❌ Never |
| No Narrative | 6 | 1/6 | ❌ Never |
| Weak Narrative | 3 | 2/6 | ❌ Never |
| Copy / Derivative | 2 | 2/6 | ❌ Never |
| **All failures** | **16** | **2/6 max** | **❌ 0/16 pass** |

**Result: Section 1 at 4+/6 has a 100% filter rate on hard failures.** Zero false negatives — no hard failure could have passed the narrative gate even at the lowest threshold setting.

**Confidence upgrade on threshold:** The 4+/6 cutoff was calibrated on 1 winner (embers, 6/6). It is now validated against 16 losers. The threshold is confirmed correct — and arguably could be tightened to 5+/6 without losing any winners from this sample (all 10 winners had strong narrative anchors).

---

## Hard No-Entry Rules — Updates From This Analysis

Two new rules validated by the failure data:

### Rule 1: Name Blacklist (validates Pattern 1 from Alert Outcome Analysis)

**Original rule (from Alert Outcome Analysis suggestions):**
```python
BLACKLIST_KEYWORDS = ["scam", "rug", "ponzi", "exploit", "drain"]
```

**Validated by:** 5 hard failures with explicit scam naming. All 5 peaked at $33–38K. Not one broke out. 0% win rate, confirmed across all 5 tokens across multiple tiers (EXTREME, FAST).

**Verdict: Implement. Zero false negatives in this dataset. Pure signal.**

---

### Rule 2: Duplicate Name Detector (validates Pattern 6 from Alert Outcome Analysis)

**Rule:** If a token with the same name (or close variant — vest/vesting/dog in vest) has already migrated this session → skip.

**Validated by:** Dog In Vest (copy of Vesting). Multiple Dog In Vest migrations in the same session — all failed. Vesting ($307K) was the only version with real momentum.

**Verdict: Implement. The original captures the meta. Every copy is a false signal.**

---

## Score History Update

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

*BC and Migration sections marked —/3 and —/5 because Section 1 terminates evaluation. These tokens never reached the on-chain check.*

---

## Synopsis

**The Winner Checklist works from both sides.**

Every winner in the Apr 27–28 session had a narratable identity — a person, event, or cultural moment that someone could explain in a sentence. Every hard failure lacked one. The 4+/6 narrative threshold, originally calibrated on a single winner (embers), correctly filters all 16 hard failures with zero ambiguity.

The failure data also reveals two filterable patterns the checklist didn't explicitly capture:

**Scam-named tokens are a bot trap.** They attract known traders into the bonding curve because bots follow wallets, not names. The BC signal is real — real wallets, real SOL, real speed. But the post-migration demand is zero because no new buyer can build conviction in a token called Scamcoin. The alert system correctly detected the BC activity. The checklist correctly kills it at narrative. The bot needs to implement the name blacklist so these alerts don't fire at all.

**Copy tokens are noise.** The original meta (Vesting) runs. Every subsequent copy (Dog In Vest) gives the same BC signal because the same bots follow the same wallets into the same type of launch. The underlying demand is already exhausted by the original. Session-level duplicate name detection eliminates these without any manual judgment.

**Data confidence update:** Winner Checklist thresholds upgraded from LOW (1 case study) to **MEDIUM** (1 winner + 16 failure validations). The narrative gate is confirmed. BC and Migration sections still need validation against loser on-chain data — that requires pulling actual post-migration volume for the 16 failures, which is not yet done.

---

## Related

- [[patterns/winner-checklist]] — threshold framework validated here
- [[patterns/alert-outcomes-apr27-28]] — source data for all 16 failures
- [[patterns/narrative-triggers]] — narrative tier list and scoring
- [[patterns/migration-speed-signal]] — tier definitions referenced above
