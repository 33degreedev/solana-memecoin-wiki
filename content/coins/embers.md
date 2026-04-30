---
name: Embers — Case Study
type: case-study
tags: [case-study, memecoin]
---

# Embers — Case Study

**Token:** embers (`C4b1rL9g4QCWUwePRLuADbbqaUv2zF8vaq6ntJ2vWbjd`)
**Date:** Apr 23, 2026
**Outcome:** ✅ WINNER — BC filled in 23 min, migrated to pumpAMM, strong post-migration demand
**Narrative type:** CEO name drop (Sam Altman) + AI mascot
**Data confidence:** HIGH (on-chain CSV + GeckoTerminal + Twitter screenshots)

---

## Full Timeline

| Time (UTC) | Event |
|-----------|-------|
| 18:34 | Sebastien Bubeck (@SebastienBubeck, OpenAI) posts GPT-5.5 TikZ unicorn — 136K views |
| 19:09:00 | Sam Altman (@sama) QTs with single word: **"embers"** — 103.7K views |
| 19:09:13 | Token launches on pump.fun — dev buys 10 SOL ($856) in same tx |
| 19:09:14 | 16 sniper wallets pile in — $7,303 in 2 seconds, 23:2 buy/sell ratio |
| 19:13 | @xacrypto1 posts token address + "ChatGPT mascot" framing — narrative crystallized |
| 19:32:14 | Bonding curve fills ($69K) → pumpAMM migration |
| 19:32:14+ | Post-migration: $2,407 volume in first 2 min, whale absorption of BC dump |

---

## Narrative Chain

| Step | Actor | Action | Impact |
|------|-------|--------|--------|
| 1 | Sebastien Bubeck | GPT-5.5 TikZ unicorn — real AI news | Hook: 136K organic views |
| 2 | Sam Altman | QTs with "embers" — names the unicorn | Catalyst: CEO-level signal, 103.7K views |
| 3 | Dev (`bwamJzzt`) | Launches token 13 seconds after Sam tweets | Supply: name = Sam's exact word |
| 4 | @xacrypto1 | Posts address + "ChatGPT mascot" frame | Distribution: simple repeatable story |

**Why it worked:** 1:1 name alignment (token = Sam's exact word), high-credibility source, organic underlying news, simple 4-word thesis ("ChatGPT's mascot").

**The 13-second anomaly:** Sam tweeted at 19:09:00 UTC, token launched at 19:09:13. Dev either had a launch staged and ready the moment Sam tweeted, or was monitoring Sam's replies in real time. Either way, the $856 dev buy at launch shows conviction.

---

## Bonding Curve Phase (19:09:13–19:32:14 UTC)

### First 2 Seconds — GeckoTerminal Data (25 unique trades)

> ⚠️ GeckoTerminal only indexed first 25 BC transactions. Full 2-min BC data requires Solscan export of `7XQvcSPmEK1Hpq5avbcXeZb9Ac4HnP1uDrNoaUxaF1HQ`.

| Metric | Value |
|--------|-------|
| Buy volume | **$7,303.73** (23 txs) |
| Sell volume | $47.92 (2 txs — 1 init, 1 flip) |
| Net | **+$7,255.81** |
| Buy/sell tx ratio | 23:2 |
| Unique buyer wallets | 16 |
| Multi-buy wallets | 5 (automated — doubled up in same second) |
| Largest sniper | `tAg2tgyH` $1,034.91 — more than the dev |

**Signal:** $7,300 in 2 seconds with 16 unique wallets = automated systems monitoring Sam Altman's replies specifically.

### Bonding Curve Summary
- Time to fill: **~23 minutes** (moderately fast — indicates real sustained demand)
- Total BC volume: ~$69K required for graduation
- Dev buy at launch: $856 (10 SOL) — seeded conviction

---

## Post-Migration Phase (19:32:14 UTC = t=0)

### Volume by 30-Second Bucket

| Window | Txs | Buy Vol | Sell Vol | Net |
|--------|-----|---------|----------|-----|
| 0–30s | 20 | $186 (12 txs) | $566 (8 txs) | **-$380 sell heavy** |
| 30–60s | 12 | $296 (11 txs) | $39 (1 tx) | **+$257 flip** |
| 60–90s | 28 | $349 (19 txs) | $340 (9 txs) | +$9 neutral |
| 90–120s | 15 | $471 (10 txs) | $160 (5 txs) | **+$311 bullish** |

**2-min total: $2,407 | Net: +$197**

### First 30 Seconds — Every Transaction

| Time | Dir | USD | Notable |
|------|-----|-----|---------|
| t+0s | BUY | $4.26 | First pumpAMM trade — sniper bot |
| t+5s | SELL | $269.58 | BC holder dumps into new liquidity |
| t+8s | BUY | $169.05 | Whale buys the dump (Flashtrade) |
| t+13–29s | BUY | $0.40 total | Bot `CYZcucbb` — 8 micro-buys at $0.08 |
| t+18s | SELL | $41.78 | BC holder exit |
| t+26s | SELL | $21.52 | Small seller |
| t+28s | SELL | $218.86 | Same whale `8Xo7so2G` flips (+29% in 20s) |
| t+29s | SELL | $10.48 | Small seller |
| t+29s | BUY | $11.41 | Fresh buyer |

### The Pattern
```
t=5s:   BC holder dump ($270) — expected, they waited 23 min
t=8s:   Whale absorbs dump ($169) — smart money signal
t=28s:  Same whale flips at +29% in 20 seconds — fastest trade in dataset
t=30s:  Sellers exhausted. 11 buys vs 1 sell in next 30s.
t=45s:  Ideal entry window — dump absorbed, flip confirmed
```

---

## Signals That Called This Winner

### Pre-Migration (Narrative)
| Signal | Value | Weight |
|--------|-------|--------|
| Source credibility | CEO + OpenAI researcher | 🟢 MAXIMUM |
| Name alignment | Token name = Sam's exact word | 🟢 PERFECT |
| Narrative simplicity | "ChatGPT mascot" — 3 words | 🟢 HIGH |
| Organic origin | Real GPT-5.5 news, not manufactured | 🟢 HIGH |
| Launch timing | 13 seconds after catalyst tweet | 🟢 TIGHT |

### Post-Migration (On-Chain)
| Signal | Value | Threshold |
|--------|-------|-----------|
| 30s volume | $752 | > $300 ✅ |
| Largest single buy | $169 | > $100 ✅ |
| Bot accumulation | 8 micro-buys from `CYZcucbb` | 3+ ✅ |
| Buy tx count vs sell | 12 > 8 | Required ✅ |
| Net sell pressure | -$380 | < -$500 ✅ |

---

## What to Learn From This

1. **The narrative window is the trade.** The profitable window was 19:09 → ~19:30 (BC phase). By migration, BC snipers were already exiting. The post-migration opportunity was smaller.
2. **Sam Altman = instant bot trigger.** 16 wallets in 2 seconds means automated systems are monitoring his replies. You can do the same manually — open Twitter, watch @sama's replies during peak hours.
3. **BC dump at migration is expected, not panic.** The $270 sell at t+5s was a BC sniper who paid ~0 relative to migration price. That dump + whale absorption at t+8s = the actual entry signal.
4. **23-min BC fill = real demand.** A fast fill (< 10 min) would be stronger. A slow fill (> 45 min) would be weaker. 23 min = moderate, sustained buying throughout BC phase.

---

## Data Gaps

| Gap | Impact |
|-----|--------|
| Full BC 2-min data (GeckoTerminal only has first 2s) | Cannot fully analyze sniper accumulation pace |
| No price reconstruction from CSV | Cannot calculate exact entry/exit prices |
| Single case study | All thresholds unvalidated — need 10–20 migrations |

---

## Sources

- `raw/C4b1rL9g_migration_apr23.md` — Solscan CSV, 1000 post-migration txs
- `raw/C4b1rL9g_narrative_apr23.md` — Twitter screenshots
- GeckoTerminal pool `7XQvcSPmEK1Hpq5avbcXeZb9Ac4HnP1uDrNoaUxaF1HQ` (BC, 25 trades)
- Launch tx: `4kZ1Deat...YUzM` (Solscan)

---

## Related Pages

- [[coins/coin-index]]
- [[patterns/narrative-triggers]]
- [[patterns/migration-signals]]
- [[patterns/volume-fingerprints]]
- [[playbooks/migration-alert]]
- [[playbooks/narrative-trade]]
