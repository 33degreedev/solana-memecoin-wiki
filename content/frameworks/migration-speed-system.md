---
title: "Migration Speed Detector System"
name: Migration Speed Detector System
type: framework
tags: [framework, system-design]
---

# Migration Speed Detector System

> **Canonical architecture:** [[frameworks/migration-detector-architecture]]
> This file is a quick-reference summary only.

---

## Core Signal Logic

```
Migration speed = time from BC pool creation → graduation ($69K MC)

PRIMARY:   migration_sec → tier → determines if we proceed
SECONDARY: known_traders in BC pool → validates demand is real
GATE:      tier ∈ {EXTREME, VERY_FAST, FAST, MODERATE} AND traders ≥ 1
```

## Tier Reference

| Tier       | BC Fill Time  | Entry     | Size     |
|------------|---------------|-----------|----------|
| EXTREME    | < 90s         | t=0       | 0.25 SOL |
| VERY_FAST  | 90s – 3min    | t=0       | 0.20 SOL |
| FAST       | 3 – 5min      | t=0       | 0.15 SOL |
| MODERATE   | 5 – 10min     | t=45s     | 0.12 SOL |
| SLOW       | 10 – 30min    | **SKIP**  | —        |
| STALLED    | > 30min       | **SKIP**  | —        |

Exit: -15% stop | +5% (50%) | +10% (50%) | 60s timer

## API Stack (Quick Reference)

```
pump.fun polling     → migration feed (30s interval)
Solscan defi/activities → BC pool txns (trader validation)
Telegram Bot API    → alert delivery (MVP)
```

⚠ Query the **BC pool address** (bonding_curve field), not the pumpAMM pool.

## Known Traders Registry

```python
KNOWN_TRADERS = {
    "4BdKaxN8G6ka4GYtQQWk4G4dZRUTX2vQH9GcXdBREFUk": {"name": "theo",    "min_buy_sol": 0.5},
    "G6fUXjMKPJzCY1rveAE6Qm7wy5U3vZgKDJmN1VPAdiZC": {"name": "clukzsol", "min_buy_sol": 0.5},
    # Add from Axiom top traders panel on winning coins
}
```

## Related

- [[frameworks/migration-detector-architecture]] — Full architecture, pseudocode, error handling, build phases
- [[patterns/migration-speed-signal]] — Tier thresholds validation data
- [[coins/chloe]] — EXTREME tier live example
- [[coins/embers]] — MODERATE tier live example
