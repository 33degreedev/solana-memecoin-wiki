---
title: "24h Report — 63 Coin Case Study — AFK Scanner Bot Signals"
name: "24h Report — 63 Coin Case Study — AFK Scanner Bot Signals"
type: case-study
tags: [case-study, memecoin, afk-scanner, bot-signals, alert-quality, narrative-analysis]
source: "/Users/grip.eth/Documents/Codex/2026-05-06/files-mentioned-by-the-user-alerts/alerts_24h_2026-05-05_2340_enriched.csv"
---

# 24h Report — 63 Coin Case Study — AFK Scanner Bot Signals

**Token:** Batch study of AFK scanner post-migration alerts  
**Date:** 2026-05-05 PT  
**Outcome:** Mixed batch: 23 / 63 reached 2x+, 5 / 63 reached 5x+, 2 / 63 reached 10x+  
**Narrative type:** Batch narrative analysis across meme, crypto-native, animal, charity, brand, AI, shock, and generic name coins  
**Data confidence:** MEDIUM-HIGH

Note: the requested report label says 65 coins, but the final enriched CSV currently contains 63 alert rows. This page analyzes all 63 rows present in the final spreadsheet.

---

## Full Timeline

| Time (PT) | Event |
|-----------|-------|
| 2026-05-05 12:55 AM–11:22 PM | AFK scanner generated post-migration alerts around the ~34K market-cap zone. |
| During alert window | Each token was classified by migration-speed tier, trader count, narrative type, post-alert ATH, current MC/FDV, and max multiple. |
| After data enrichment | DexScreener was used for current MC/FDV and GeckoTerminal minute OHLCV was used for post-alert ATH reconstruction. |
| Final analysis | Narrative fields were added to every row: category, hook, strength, and notes. |

---

## Narrative Chain

| Step | Actor | Action | Impact |
|------|-------|--------|--------|
| 1 | AFK scanner bot | Detected migrated tokens around the early market-cap zone. | Produced a broad alert batch with many weak/generic names and a small number of high-quality narratives. |
| 2 | Known trader set | Appeared in bonding-curve or early post-migration context. | Trader count alone did not guarantee performance; 1-2 trader alerts were better than 3+ trader alerts in this sample. |
| 3 | Market/narrative layer | Tokens with recognizable, repeatable hooks separated from generic names. | Strong narratives produced every 5x+ runner in the dataset. |
| 4 | Exit strategy | Different TP ladders were simulated. | Buying all alerts was not profitable; filtered entries plus a 3x/5x/10x ladder performed best. |

**Why it worked / failed:** The scanner captured real opportunity, but not enough to justify buying every alert. The winning subset needed a recognizable narrative hook and reasonable migration-speed/trader-count context. The strongest outcome cluster came from FAST/MOD tier alerts with 1-2 traders and strong narratives. Weak names could still produce 2x moves, but none produced 5x+ runners.

---

## Bonding Curve Phase

> Data source: final enriched alert CSV; original BC details were not included in the spreadsheet.

| Metric | Value |
|--------|-------|
| Time to fill | Represented only as migration-speed tier: EXTREME, VERY_FAST, FAST, MODERATE, MID, SLOW |
| Dev buy at launch | Not available |
| First 30s volume | Not available |
| Buy/sell ratio (first 30s) | Not available |
| Unique wallets (first 30s) | Not available |
| Multi-buy wallets | Not available |

Tier thresholds used:

| Tier | Migration-Speed Bucket |
|---|---|
| EXTREME | 0-1.5m |
| VERY_FAST | 1.5-3m |
| FAST | 3-5m |
| MODERATE | 5-10m |
| MID | 10-15m |
| SLOW | 15-20m |
| STALLED | 20m+ skipped |

---

## Post-Migration Phase

> Data source: final enriched alert CSV using DexScreener current MC/FDV and GeckoTerminal minute OHLCV.

### Batch Outcome Summary

| Threshold | Alerts Hit | Rate |
|---|---:|---:|
| 1.5x+ post-alert | 37 / 63 | 58.7% |
| 2x+ post-alert | 23 / 63 | 36.5% |
| 5x+ post-alert | 5 / 63 | 7.9% |
| 10x+ post-alert | 2 / 63 | 3.2% |

### Narrative Strength Results

| Narrative Strength | Count | 2x+ Winners | 5x+ Runners | Median Max Multiple |
|---|---:|---:|---:|---:|
| Strong | 10 | 7 | 5 | 5.45x |
| Medium | 25 | 7 | 0 | 1.59x |
| Weak | 28 | 9 | 0 | 1.48x |

Key read: all 5 main runners came from the Strong narrative group. Medium and Weak narratives still produced tradable 2x moves, but no 5x+ runners.

---

## 63-Coin Case Table

| # | Token | Tier | Traders | Narrative | Strength | Alert MC | ATH MC | Current MC | Max | Outcome |
|---:|---|---|---:|---|---|---:|---:|---:|---:|---|
| 1 | YOLO / You Only Live Once | MID | 1 | Life motto / relatable meme | Medium | $35,270 | 50K | 3K | 1.41x | Loser |
| 2 | LOBBYOOR / Bitcoin Policy Institute | MID | 1 | Bitcoin / policy / institution parody | Medium | $35,865 | 146K | 58K | 4.07x | 2x+ winner |
| 3 | Bao Bao / Justice for Bao Bao | MID | 1 | Justice / sympathy / character | Medium | $35,041 | 43K | 3K | 1.21x | Loser |
| 4 | NIGGA / NvidiaIntelGoogleGmeApple | MID | 1 | Shock / mega-cap tech acronym | Weak | $35,094 | 64K | 4K | 1.82x | 1.5x+ small win |
| 5 | WILL / Will Roberts | MID | 1 | Person-name coin | Weak | $35,418 | 116K | 12K | 3.28x | 2x+ winner |
| 6 | IMAPCOIN / IMAPCOIN | EXTREME | 1 | Generic coin / unclear | Weak | $47,774 | 57K | 2K | 1.19x | Loser |
| 7 | updog / updog | EXTREME | 1 | Classic internet joke | Medium | $4,333 | 5K | 306 | 1.18x | Loser |
| 8 | Blind / End My Blindness | MID | 4 | Charity / medical sympathy | Medium | $30,595 | 71K | 6K | 2.31x | 2x+ winner |
| 9 | OBTs / Outcome Based Tokens | FAST | 1 | Crypto meta / tokenomics | Medium | $11,627 | 38K | 34K | 3.24x | 2x+ winner |
| 10 | Alzheimers / Buy & Forget | MODERATE | 2 | Dark humor / memory joke | Strong | $33,227 | 286K | 176K | 8.62x | 5x+ runner |
| 11 | CHILLBASS / Just a chill bass | MID | 1 | Animal chill meme | Medium | $48,246 | 82K | 7K | 1.71x | 1.5x+ small win |
| 12 | MSTR / Strategy BTC | FAST | 1 | Bitcoin treasury / MSTR parody | Strong | $33,665 | 43K | 2K | 1.27x | Loser |
| 13 | GOONCOIN / GOONCOIN | VERY_FAST | 2 | Shock / adult degen meme | Weak | $31,689 | 43K | 4K | 1.37x | Loser |
| 14 | PSTR / Ponzi Strategy | MODERATE | 1 | Ponzi / crypto meta satire | Medium | $31,239 | 37K | 2K | 1.17x | Loser |
| 15 | FART / FosterAdoptRescueTransport | MID | 3 | Acronym / animal rescue charity | Medium | $35,125 | 41K | 2K | 1.18x | Loser |
| 16 | BOY / Trader Boy | EXTREME | 1 | Trader identity / mascot | Weak | $35,611 | 43K | 2K | 1.20x | Loser |
| 17 | SELLOR / Michul Sellor | MODERATE | 2 | Michael Saylor parody | Strong | $35,527 | 858K | 495K | 24.15x | 5x+ runner |
| 18 | armweak / brian armweak | EXTREME | 3 | Person parody / wordplay | Medium | $35,215 | 50K | 2K | 1.42x | Loser |
| 19 | Wikipetan / Wikipetan | MID | 1 | Anime / internet mascot | Medium | $36,617 | 47K | 20K | 1.28x | Loser |
| 20 | UPWARD / Onward and Upward | EXTREME | 1 | Motivational phrase | Weak | $24,616 | 42K | 2K | 1.72x | 1.5x+ small win |
| 21 | Apu / Voice Of Apu | VERY_FAST | 4 | Pepe/Apu meme | Medium | $34,129 | 39K | 2K | 1.15x | Loser |
| 22 | Moonie / Moonie | SLOW | 1 | Moon / mascot | Weak | $35,356 | 46K | 2K | 1.30x | Loser |
| 23 | CHADAM / Chadam Mcbride | VERY_FAST | 1 | Chad/person-name meme | Weak | $35,387 | 72K | 6K | 2.03x | 2x+ winner |
| 24 | NEVER / Never Looked Back | EXTREME | 2 | Motivational / regret phrase | Weak | $34,816 | 54K | 2K | 1.55x | 1.5x+ small win |
| 25 | DENALI / The Denali Puppies | SLOW | 1 | Animal / puppies | Medium | $154,559 | 268K | 9K | 1.74x | 1.5x+ small win |
| 26 | asset / One Asset. Endless possibilities | FAST | 2 | Asset / finance meta | Medium | $27,471 | 42K | 2K | 1.53x | 1.5x+ small win |
| 27 | NICE / National Immigration and Customs | EXTREME | 1 | Politics / agency acronym | Medium | $33,610 | 80K | 3K | 2.38x | 2x+ winner |
| 28 | NICE / NICE | EXTREME | 1 | Positive adjective / generic | Weak | $33,576 | 106K | 2K | 3.16x | 2x+ winner |
| 29 | LOVE / Spreading Love | MODERATE | 1 | Positive emotion / love | Weak | $35,397 | 36K | 2K | 1.00x | Loser |
| 30 | EBAY / eBay | MODERATE | 2 | Brand parody | Medium | $32,604 | 97K | 3K | 2.97x | 2x+ winner |
| 31 | MILLY / milly | EXTREME | 1 | Person/pet name | Weak | $33,982 | 36K | 3K | 1.07x | Loser |
| 32 | AI / Artificial Inu | FAST | 3 | AI + dog/inu | Strong | $34,659 | 216K | 14K | 6.24x | 5x+ runner |
| 33 | AI / Artificial Inu | FAST | 1 | AI + dog/inu | Strong | $31,449 | 211K | 74K | 6.69x | 5x+ runner |
| 34 | CUM / Cum | EXTREME | 1 | Shock / adult meme | Weak | $41,462 | 79K | 3K | 1.90x | 1.5x+ small win |
| 35 | REMY / Remy | MODERATE | 4 | Character / pet name | Weak | $35,033 | 45K | 11K | 1.29x | Loser |
| 36 | Finuts / Finuts | FAST | 1 | Food / finance pun | Weak | $31,529 | 42K | 2K | 1.32x | Loser |
| 37 | WIGGER / Wigger Planet | MODERATE | 3 | Shock / planet meme | Weak | $32,018 | 45K | 2K | 1.41x | Loser |
| 38 | NOTFINE / This Is Not Fine | MODERATE | 2 | This is fine derivative | Strong | $35,032 | 35K | 2K | 1.00x | Loser |
| 39 | JOHN / Long John | EXTREME | 2 | Person-name / innuendo | Weak | $34,541 | 89K | 4K | 2.56x | 2x+ winner |
| 40 | LUKE / Luke Battles Cancer Fund | SLOW | 1 | Charity / cancer sympathy | Strong | $33,353 | 142K | 4K | 4.26x | 2x+ winner |
| 41 | Frank / FrankFrankFrank | MODERATE | 3 | Repetition / name meme | Weak | $33,660 | 40K | 2K | 1.20x | Loser |
| 42 | ISLAND / The Easter Island Theory | EXTREME | 3 | Ancient mystery / theory | Medium | $34,172 | 59K | 3K | 1.73x | 1.5x+ small win |
| 43 | 1 / 1 min a day | SLOW | 1 | Self-improvement / habit | Strong | $29,339 | 137K | 3K | 4.66x | 2x+ winner |
| 44 | GRIFFIN / Experiment A51 | SLOW | 2 | Experiment / sci-fi | Medium | $33,602 | 85K | 4K | 2.52x | 2x+ winner |
| 45 | PEPTB / Peptbase | EXTREME | 2 | Peptide / biotech | Medium | $35,021 | 42K | 2K | 1.19x | Loser |
| 46 | Water / Water Coin | EXTREME | 1 | Elemental / basic commodity | Weak | $32,256 | 70K | 3K | 2.18x | 2x+ winner |
| 47 | EAGLE / Big Bear Bald Eagle | EXTREME | 2 | Animal / livestream-style eagle | Medium | $34,479 | 68K | 8K | 1.96x | 1.5x+ small win |
| 48 | OREO / Oreo Token | EXTREME | 1 | Brand/food parody | Medium | $34,217 | 60K | 2K | 1.77x | 1.5x+ small win |
| 49 | journey / journey has barely started | EXTREME | 2 | Motivational / journey | Weak | $29,428 | 72K | 2K | 2.46x | 2x+ winner |
| 50 | TOLY / Crypto Daddy | FAST | 3 | Solana founder / crypto personality | Strong | $29,834 | 41K | 2K | 1.39x | Loser |
| 51 | Roho / Roho | MODERATE | 1 | Name / mascot | Weak | $27,417 | 91K | 6K | 3.31x | 2x+ winner |
| 52 | Kaiser / Kaiser | EXTREME | 2 | Name / authority figure | Weak | $33,709 | 93K | 3K | 2.75x | 2x+ winner |
| 53 | turdcoin / turdcoin | EXTREME | 1 | Gross-out meme | Weak | $24,872 | 29K | 2K | 1.18x | Loser |
| 54 | turdcoin / turdcoin | EXTREME | 1 | Gross-out meme | Weak | $32,572 | 141K | 24K | 4.34x | 2x+ winner |
| 55 | Sakura / Sakura-chan | FAST | 2 | Japanese/anime character | Medium | $34,759 | 54K | 3K | 1.54x | 1.5x+ small win |
| 56 | FUND5 / Crypto Fund 5 | FAST | 3 | Crypto fund / finance meta | Medium | $33,877 | 54K | 6K | 1.59x | 1.5x+ small win |
| 57 | Bartleby / The Nietzschean Dog | EXTREME | 1 | Dog + philosophy | Medium | $26,540 | 41K | 2K | 1.53x | 1.5x+ small win |
| 58 | FREEMIND / Freemind | MODERATE | 1 | Mindset / freedom | Weak | $35,037 | 40K | 2K | 1.15x | Loser |
| 59 | FREEMAN / Freeman | FAST | 1 | Freedom / person-name | Weak | $9,424 | 18K | 2K | 1.89x | 1.5x+ small win |
| 60 | FREEMAN / Freeman | EXTREME | 2 | Freedom / person-name | Weak | $33,653 | 47K | 2K | 1.40x | Loser |
| 61 | Walleo / Walleo | SLOW | 3 | Mascot / name coin | Weak | $33,370 | 33K | 2K | 0.97x | Loser |
| 62 | wrdog / World Record Dog | FAST | 1 | Animal / record story | Strong | $31,882 | 538K | 89K | 16.87x | 5x+ runner |
| 63 | PATAPIM / Brrr Brrr Patapim | MODERATE | 1 | Italian brainrot / viral character | Medium | $33,928 | 87K | 20K | 2.56x | 2x+ winner |

---

## Signals Present / Absent

### Narrative

| Signal | Present? | Notes |
|--------|----------|-------|
| High-credibility source | Partial | Only inferred from names/narratives in the spreadsheet; no direct social/news source was included. |
| Name alignment | Strong in winners | SELLOR, wrdog, Alzheimers, Artificial Inu, 1 min a day, and LUKE had clear name-to-thesis alignment. |
| Simple repeatable thesis | Strong in runners | Every 5x+ runner had a simple retellable hook. |
| Organic underlying event | Unknown | Requires Twitter/news/social verification not present in the CSV. |
| Shock-only naming | Present but weak | Shock/adult/offensive names generated attention but no 5x+ runners. |
| Generic name coins | Present and noisy | Many weak names reached small moves but did not produce main runners. |

### On-Chain / Scanner Signals

| Signal | Value | Pass? |
|--------|-------|-------|
| Migration-speed tier captured | Yes | Pass |
| Trader count captured | Yes | Pass |
| Current MC/FDV captured | Yes | Pass |
| Post-alert ATH captured | Yes | Pass |
| Full intratrade path | No | Gap |
| First 30s post-migration volume | No | Gap |
| Buy/sell ratio | No | Gap |
| Smart-wallet identity quality score | Partial | Trader names available, but no weighted score in this sheet. |

---

## Key Lessons

1. Strong narrative was the clearest differentiator for main runners. Strong narratives were only 10 / 63 alerts but produced all 5 of the 5x+ runners.
2. Medium and Weak narratives can still produce tradable 2x moves, but they should not be treated as main-runner candidates without extra confirmation.
3. Migration-speed tier alone is insufficient. FAST/MOD mattered most for 5x+ runners, but narrative strength decided which names actually ran.
4. Trader count alone is insufficient. 1-trader alerts produced major runners, while 3+ trader alerts underperformed in this batch.
5. The AFK scanner should separate "tradable 2x opportunity" from "main runner candidate." The filters are not the same.
6. Current best working strategy from this batch: filter FAST/MOD with 1-2 traders, prefer Strong narrative, first initials at 3x, then 5x/10x runner ladder.

---

## Data Gaps

| Gap | Impact |
|-----|--------|
| Source file contains 63 rows, not 65 | Report title preserves user wording, but analysis covers the available 63 rows only. |
| No launch/BC transaction detail | Cannot score dev buy, early wallet count, first 30s volume, or buy/sell imbalance. |
| No social source URLs | Narrative classification is inferred from ticker/name rather than verified catalysts. |
| No intratrade low path | Stop-loss and risk-control simulations remain approximate. |
| No trader quality weighting | Trader names are available, but the report does not yet score individual trader reliability. |

---

## Sources

- `/Users/grip.eth/Documents/Codex/2026-05-06/files-mentioned-by-the-user-alerts/alerts_24h_2026-05-05_2340_enriched.csv`
- `/Users/grip.eth/Documents/Codex/2026-05-06/files-mentioned-by-the-user-alerts/alerts_24h_2026-05-05_2340_enriched.xlsx`

---

## Related Pages

- [[coins/coin-index]]
- [[patterns/alert-outcomes-may05-2026]]
- [[patterns/narrative-triggers]]
- [[patterns/migration-signals]]
- [[patterns/migration-speed-signal]]
- [[patterns/volume-fingerprints]]
