---
title: "Migration Speed Detector — Implementation Checklist"
name: Migration Speed Detector — Implementation Checklist
type: framework
tags: [framework, system-design]
---

# Migration Speed Detector — Implementation Checklist

> **Canonical architecture:** [[frameworks/migration-detector-architecture]]
> This file tracks build progress only.

---

## Validation (Pre-Build)

Real data confirming the system design works:

| Coin     | BC Fill Time | Tier     | Known Traders       | Result             |
|----------|--------------|----------|---------------------|--------------------|
| chloe    | 76 seconds   | EXTREME  | 49 wallets, 1s      | ✅ $1.68M ATH      |
| embers   | 23 minutes   | MODERATE | 16 wallets, 2s      | ✅ $6.93K winner   |

Insight: Both tiers win. Narrative + speed + traders = full signal. Speed correlates with
ATH ceiling (faster = higher peak) but is not a gate by itself.

---

## Phase 1 — MVP Checklist

- [ ] pump.fun polling loop (30s interval, filter migrated, last 5min window)
- [ ] Migration time calculation (`migrated_at - created_at`)
- [ ] Tier classification (EXTREME / VERY_FAST / FAST / MODERATE / SLOW / STALLED)
- [ ] ALERT_CACHE dedup (in-memory dict, CA → alert metadata)
- [ ] Solscan BC pool query (`/account/defi/activities`, filter ACTIVITY_TOKEN_SWAP)
- [ ] Known traders registry matching (wallet + min_buy_sol threshold)
- [ ] Telegram alert delivery with Markdown formatting
- [ ] Manual backtest: verify chloe and embers would have triggered

## Phase 2 — Hardening

- [ ] Birdeye fallback when pump.fun is down
- [ ] Solscan rate limit handling (60s backoff on 429)
- [ ] Persistent ALERT_CACHE (SQLite, survives restarts)
- [ ] Structured logging: alerts fired, discard reasons, latencies
- [ ] Discord webhook (second delivery channel)

## Phase 3 — Live Calibration (Week 1)

- [ ] Deploy and run for 5 days
- [ ] Log: every alert → entry price, peak, outcome, PnL
- [ ] Measure false positive rate (target < 20%)
- [ ] Tune min_buy_sol if too noisy
- [ ] Expand KNOWN_TRADERS list from Axiom panels

## Phase 4 — Enhancement (Week 2+)

- [ ] RPC event listener for sub-10s latency
- [ ] Narrative score integration
- [ ] Dynamic position sizing: speed_tier × narrative_score composite
- [ ] Auto-execute webhook (optional)

---

## Success Metrics After Week 1

| Metric              | Target     |
|---------------------|------------|
| Alerts / day        | 2–4        |
| Alert latency       | < 60s      |
| False positive rate | < 20%      |
| True positive rate  | > 60%      |

---

## Related

- [[frameworks/migration-detector-architecture]] — Full architecture and pseudocode
- [[frameworks/migration-speed-system]] — Quick-reference summary
