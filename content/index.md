---
title: Solana Memecoins Wiki
---

# Solana Memecoins Wiki

Research wiki for Solana memecoin trading — migration detection, wallet tracking, narrative analysis, and post-mortem breakdowns. Built from live bot data and on-chain analysis.

---

## Case Studies

Token launches dissected with full timelines, on-chain data, and signal analysis.

- [[coins/24h-report-65-coin-case-study-afk-scanner-bot-signals|24h Report — 65 Coin Case Study — AFK Scanner Bot Signals]] — May 5 AFK scanner batch, 63 available rows, narrative strength and TP lessons
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

## Bot Stats (Apr 29, 2026)

| Metric | Value |
|---|---|
| Tracked wallets | 24 (all Tier S) |
| Detection paths | 3 (Pre-watch, RPC scan, Post-migration) |
| Speed tiers | 6 (EXTREME → STALLED) |
| Top alert traders | dv (11), parsiix (6), chester (5), theo (4) |
| Best win rate | EXTREME 57%, parsiix 80% |
