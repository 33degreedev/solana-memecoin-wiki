---
name: Volume Fingerprints — Pattern Library
type: pattern
tags: [pattern, signal]
---

# Volume Fingerprints — Pattern Library

> **Data confidence: LOW** — Based on 1 confirmed case (embers). These are baseline fingerprints, not validated rules.

What does volume look like on a winning coin in the first seconds, minutes, and hours? This page tracks volume patterns across studied coins.

---

## What Is a Volume Fingerprint?

A volume fingerprint is the characteristic shape of buying/selling activity over time. Winners have distinct fingerprints at each phase — you can learn to recognize them before committing.

---

## Phase 1: Bonding Curve Launch (First 2 Seconds)

### embers — Apr 23, 2026 ✅

| Metric | Value |
|--------|-------|
| Block 1 (t=0s) | Dev buy $843 + 2 init txs |
| Block 2 (t=1s) | 16 unique wallets, 23 buys, $6,461 |
| Buy/sell ratio | 23:2 |
| Largest single buy | $1,035 (sniper > dev buy) |
| Multi-buy wallets | 5 (automated) |
| Net flow | +$7,256 |

**Fingerprint:** Explosive buy-only first second, dev buy immediately followed by automated sniper wave. Zero organic selling — all sells are either init txs or immediate flips.

**What this indicates:** Automated systems detected a high-quality narrative trigger (Sam Altman tweet) before most humans could react. The 5 wallets that bought twice in the same block are bots with pre-programmed conviction thresholds.

---

## Phase 2: Bonding Curve (Full Phase — embers)

> Only first 2 seconds recoverable from GeckoTerminal. Full data requires Solscan export.

| Metric | Value |
|--------|-------|
| Total BC duration | 23 minutes |
| Total BC volume | ~$69K (graduation threshold) |
| Implied avg/min | ~$3K/min |

**Fingerprint shape:** Strong opening burst → sustained buying over 23 min → graduation. The opening burst (>$7K in 2s) suggests the sustained buying was real community demand, not just a momentary spike.

---

## Phase 3: Post-Migration (First 2 Minutes)

### embers — t=0 to t=120s

| Window | Buy Vol | Sell Vol | Net | Shape |
|--------|---------|----------|-----|-------|
| 0–30s | $186 | $566 | -$380 | SELL HEAVY (BC dump) |
| 30–60s | $296 | $39 | +$257 | BUY FLIP |
| 60–90s | $349 | $340 | +$9 | NEUTRAL |
| 90–120s | $471 | $160 | +$311 | BULLISH BUILD |

**Fingerprint:** J-curve. Sell pressure front-loaded (BC holders exiting), followed by progressive buy dominance as sellers exhaust. The flip at 30s is the signal.

**The J-curve pattern:**
```
Volume
  |  S S S                    ← BC holders dump (expected)
  |      B B S B B B B B      ← whale absorbs, bots accumulate
  |              B B B B B    ← retail follows
  |________________________
  0s   30s   60s   90s  120s
```

---

## Volume Ratios That Signal Strength

Based on embers only — needs validation:

| Ratio | embers | Suggested Threshold |
|-------|--------|-------------------|
| BC first 2s buy% | 99.3% | > 90% = extreme launch signal |
| Post-migration 30s buy tx count / sell tx count | 12/8 = 1.5× | > 1.0× required |
| Post-migration 30s total volume | $752 | > $300 |
| 60–120s net vs 0–60s net | +$320 vs -$123 | Min 2 = improving trend |

---

## What Bad Volume Looks Like (Hypothesized)

Not yet confirmed with a loss case study. Based on reasoning:

| Signal | Bad Pattern |
|--------|------------|
| Post-migration first 30s sell % | > 80% — overwhelming BC exit, no absorption |
| Largest single buy in first 30s | < $50 — no smart money |
| Volume trend 0–30s vs 30–60s | Declining — momentum dying |
| Unique buy wallets in first 30s | < 3 — manipulation risk |
| Net sell pressure | > -$1,000 — coordinated dump |

---

## Volume as a Confirmation Tool

Volume doesn't call a winner alone — it confirms a narrative. The correct sequence:

1. **Narrative triggers** (CEO tweet, AI milestone, etc.) → see [[patterns/narrative-triggers]]
2. **BC signals** (fill speed, sniper wave) confirm the narrative has traction
3. **Post-migration volume** confirms the market absorbed the BC dump
4. **Entry signal** at t=45s when flip confirmed

Volume that appears without a narrative is weaker — more likely to be manipulated or temporary.

---

## Building the Database

For each new coin studied, record:

| Field | Where to find |
|-------|--------------|
| BC first 30s buy vol | Solscan BC account export |
| BC first 30s buy% | Calculate from export |
| Post-migration 0–30s buy vol | Solscan pumpAMM export |
| Post-migration 0–30s buy tx count | Count from export |
| Largest single buy (30s) | Max of buy column |
| Net flow (30s) | Buy vol - Sell vol |
| Time to flip (net turns positive) | Find first positive 30s bucket |

---

## Related Pages

- [[coins/coin-index]]
- [[patterns/migration-signals]]
- [[patterns/narrative-triggers]]
- [[patterns/winner-checklist]]
- [[playbooks/migration-alert]]
