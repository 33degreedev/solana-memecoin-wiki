---
title: Solana Memecoins Wiki
---

# Solana Memecoins Wiki

Research wiki for Solana memecoin trading — migration detection, wallet tracking, narrative analysis, and post-mortem breakdowns. Built from live bot data and on-chain analysis.

---

## Case Studies

Token launches dissected with full timelines, on-chain data, and signal analysis.

- [[coins/24h-report-65-coin-case-study-afk-scanner-bot-signals|24h Batch Report — 63 Coins]] — May 5 AFK scanner batch, 63 alert rows, narrative strength and TP lessons
- [[coins/home-solana-apr2026|HOME — Solana Is Home]] — EXTREME migration (17s), @solana catalyst, west + jijo in BC
- [[coins/sve-sam-vs-elon-apr2026|SVE — Sam Vs. Elon]] — STALLED migration (40m), parsiix + bandit BC accumulation, BC_PRE_WATCHLIST origin story
- [[coins/aib-america-is-back|AIB — America Is Back]] — Trump speech catalyst, three competing tokens, vamping case study
- [[coins/chloe|Chloe]] — video-embedded trigger from Nikita Bier's 1M follower milestone, name spoken not typed
- [[coins/embers|Embers]] — Sam Altman one-word tweet, 23min BC fill, 16 snipers in first 2 seconds
- [[coins/coin-index|Coin Index]] — full token registry

---

## Frameworks

System architecture, detection logic, and analytical models.

- [[frameworks/migration-detector-how-it-works|Migration Detector — How It Works]] — full bot architecture, three detection paths, tier thresholds, Make A Wish investigation
- [[frameworks/migration-detector-architecture|Migration Detector Architecture]] — system design and BC_PRE_WATCHLIST
- [[frameworks/migration-speed-system|Migration Speed Detector System]] — speed tier classification
- [[frameworks/migration-speed-implementation|Migration Speed Detector Implementation]] — implementation details
- [[frameworks/farmer-detection|Farmer Detection Framework]] — identifying leaderboard farmers vs. real traders
- [[frameworks/trade-deconstruction|Trade Deconstruction Framework]] — learning from trader behavior
- [[frameworks/position-sizing|Position Sizing & Volume Efficiency]] — sizing models
- [[frameworks/data-extraction-proposals|Data Extraction Proposals]] — Reddit, X, and wallet discovery pipelines

---

## Patterns

Recurring signals, post-mortems, and statistical analysis from live sessions.

- [[patterns/two-day-alert-system-review-may05-may06-2026|Two-Day Alert System Review — May 5–6, 2026]] — combined tier settings, trader attribution, 10x+ runner analysis, and filters to test next
- [[patterns/alert-outcomes-may06-2026|Alert Outcome Analysis — May 6, 2026]] — 45-row AFK scanner skip-rule test, including skipped-vs-alerted hit rates and EXTREME/STALLED policy notes
- [[patterns/alert-outcomes-may05-2026|Alert Outcome Analysis — May 5, 2026]] — 63 alert batch, 36.5% 2x hit rate, narrative strength and TP lessons
- [[patterns/alert-outcomes-apr29|Alert Outcome Analysis — Apr 29, 2026]] — 26 alerts, 38% win rate, 10 winners
- [[patterns/alert-outcomes-apr27-28|Alert Outcome Analysis — Apr 27–28, 2026]] — first session analysis
- [[patterns/hard-failure-postmortem-apr2026|Hard Failure Post-Mortem — Apr 2026]] — why losers failed
- [[patterns/winner-checklist|Winner Checklist]] — go/no-go decision framework
- [[patterns/migration-signals|Migration Signals]] — what predicts post-migration runs
- [[patterns/migration-speed-signal|Migration Speed Signal]] — speed tier vs. outcome data
- [[patterns/narrative-triggers|Narrative Triggers]] — catalyst types and strength
- [[patterns/volume-fingerprints|Volume Fingerprints]] — on-chain volume patterns
- [[patterns/vamping|Vamping Framework]] — token revival detection

---

## Playbooks

Actionable trading strategies derived from the research.

- [[playbooks/migration-alert|Migration Alert Playbook]] — how to trade bot alerts
- [[playbooks/narrative-trade|Narrative Trade Playbook]] — narrative-driven entries
- [[playbooks/theo-style|Theo Style Playbook]] — replicating Theo's approach

---

## Traders

Wallet analysis and trading style breakdowns for tracked wallets.

- [[traders/theo|Theo]] — high-conviction narrative trader
- [[traders/jijo|Jijo]] — BC sniper, automated execution
- [[traders/cented|Cented]] — leaderboard analysis

---

## Bot Stats (May 5–6, 2026 — two-day combined)

| Metric | Value |
|---|---|
| Tracked wallets | 24 (all Tier S) |
| Detection paths | 3 (Pre-watch, RPC scan, Post-migration) |
| Speed tiers | 6 (EXTREME → STALLED) + MID emerging |
| Alerts analysed | 108 across 2 days |
| 2x+ hit rate | 38.9% (42/108) |
| 5x+ hit rate | 11.1% (12/108) |
| 10x+ main runners | 2.8% (3/108) — all from strong narratives |
| Best tier for runners | FAST + MODERATE (all 3 main runners) |
