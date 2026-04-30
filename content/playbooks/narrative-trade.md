---
title: "Narrative Trade Playbook — How to Trade Narrative Coins"
name: Narrative Trade Playbook — How to Trade Narrative Coins
type: playbook
tags: [playbook, strategy]
---

# Narrative Trade Playbook — How to Trade Narrative Coins

> **Based on:** [[coins/embers]] (single confirmed case). Framework is logical; execution requires practice.

A narrative trade is triggered by an external event (tweet, news, cultural moment) that gives a memecoin a story. This playbook covers how to spot them, evaluate them, and trade them before the window closes.

---

## The Narrative Trade in One Sentence

**Someone credible says a word → a coin with that name launches → you buy before the story spreads → you sell when the story peaks.**

The window from tweet to "everyone knows about it" is 10–60 minutes. Everything before that window is the trade.

---

## Step 1 — Monitoring for Triggers

**Who to watch:**
- Sam Altman (@sama) — OpenAI CEO, 35M+ followers
- Elon Musk (@elonmusk) — any crypto or meme-adjacent content
- Vitalik Buterin (@VitalikButerin) — Ethereum ecosystem
- Key AI researchers with large followings (> 500K)
- Trending crypto KOLs (> 100K followers, crypto-native)

**What to watch for:**
- A single evocative word or short phrase in a reply/quote tweet
- Content about AI, new model releases, tech milestones
- Cultural moments that map to memeable names

**Alert method:**
- Turn on Twitter/X notifications for specific accounts
- Use TweetDeck or similar to monitor reply chains
- Scan Crypto Twitter timeline manually during peak hours (17:00–23:59 UTC)

---

## Step 2 — Evaluate the Narrative (< 5 minutes)

Use Section 1 of [[patterns/winner-checklist]]:

```
[ ] Source is verifiable (not anonymous)
[ ] Source has 1M+ followers OR is a known CEO/founder
[ ] Token name = exact word or phrase from the source
[ ] Underlying event is organic (not manufactured for the coin)
[ ] Thesis fits in 1 sentence without jargon
[ ] Name has lore / meaning / cultural depth

SCORE: ___ / 6
< 4: Stop.   4–5: Proceed.   6: High conviction.
```

**Time to complete:** 60–90 seconds. You don't have longer than this.

---

## Step 2b — Check for Vamping

Before searching for a single coin, check if multiple coins with the same name exist.

```
Search DexScreener / Axiom for the exact narrative word(s).
Count how many tokens appear with same/similar name.

1 token → proceed to Step 3 (standard single-coin flow)
2+ tokens → VAMPING SCENARIO. Go to [[patterns/vamping]] before entering anything.
```

**Political figure narratives (Trump, Elon, major politicians) almost always generate vamping.** Expect 2–4 competing coins and apply the vamping decision framework before committing to any position.

---

## Step 3 — Find the Token

Search pump.fun and DexScreener for the exact word from the tweet.

```
DexScreener → Search "[word]" → Filter: Solana, new pairs, launched < 30 min ago
pump.fun → Search "[word]" → Check bonding curve %

Look for:
✅ Token name matches the exact word from the tweet
✅ Launched within 30 minutes of the tweet
✅ BC < 50% filled (you're not too late)
✅ Dev bought at launch (Solscan launch tx)

If multiple tokens with same name: take the one launched closest to the tweet.
If BC is > 70% filled: evaluate quickly — migration may be imminent.
```

---

## Step 4 — Check the Linking Account

Who is connecting the tweet to the token address? Evaluate them:

```
Good signs:
✅ Account > 50K followers
✅ Crypto-native profile (quant, analyst, trader)
✅ Has done this before (check their timeline)
✅ Posts with the Merriam-Webster or context embed (lore building)

Red flags:
❌ Account < 30 days old
❌ Account has < 500 followers
❌ Account first post ever is the linking tweet
❌ Account is anonymous with no history
```

If no linking account exists yet — you are the linking account. You spotted it first.

---

## Step 5 — On-Chain Validation

### If BC is still active:

Check Section 2 of [[patterns/winner-checklist]]:
- BC fill time pace (is it filling fast?)
- Dev buy visible in launch tx
- Multiple snipers visible in first Solscan transactions

If BC fills fast (< 15 min) with strong early buying: **you can enter during BC phase** — higher risk, higher reward.

### If just migrated to pumpAMM:

Follow [[playbooks/migration-alert]] — evaluate at t=30s, enter at t=45s.

---

## Step 6 — Entry

| Phase | Entry timing | Risk | Reward | Condition |
|-------|-------------|------|--------|-----------|
| BC phase (early) | Within 10 min of narrative | High | Very high | Narrative score 5–6/6, BC < 20% filled |
| BC phase (late) | BC 50–80% filled | Medium | Medium | BC filling fast, narrative confirmed |
| Post-migration | t=45s post-migration | Lower | Lower | Migration signals 4+/5 |

**Position sizing:** Always use [[playbooks/theo-style]] sizing rules (5% of capital). Narrative does not justify oversizing.

---

## Step 7 — Exit

**Narrative trades have a limited window.** The story peaks when:
1. The source (CEO, celebrity) comments on or denies the coin
2. Major crypto media picks it up (Decrypt, CoinDesk)
3. The BC fills and post-migration volume normalizes

**Exit strategy:**
- If trading the BC phase: exit when BC approaches 80% or when volume starts declining
- If trading post-migration: follow theo exit rules (60s timer, +5%/+10% targets)
- Never hold a narrative trade waiting for "the next leg up" — narrative fades fast

**Hard exit triggers:**
- ❌ The source denies or ignores the coin → sell immediately
- ❌ Volume drops 50%+ from peak → trend is over
- ❌ 60-second timer (if using theo system)

---

## The Narrative Timeline (embers Example)

```
18:34 UTC   Bubeck posts GPT-5.5 unicorn        → Hook exists
19:09 UTC   Sam Altman tweets "embers"          → TRIGGER: 0 mins
19:09:13    Token launches                       → Enter: BC phase
19:13 UTC   @xacrypto1 frames narrative         → +4 min: story spreading
19:32:14    Migration to pumpAMM                → +23 min: BC filled
19:32–19:34 Post-migration entry window         → +23–25 min: last entry
~19:45      Narrative widely known in CT        → Window closing
```

**The entire profitable window: ~36 minutes from tweet to end of migration window.**

---

## Common Mistakes

| Mistake | Why It's Costly |
|---------|----------------|
| Entering on weak narrative (score < 4/6) | Not enough traction to fill BC |
| Entering when BC is already 80%+ filled | Migration is minutes away — no BC phase alpha |
| Oversizing because "Sam Altman named it" | Narrative doesn't override position sizing rules |
| Holding past migration for "next leg up" | Post-migration has lower EV than BC phase |
| Ignoring on-chain signals (only narrative) | Narrative without volume = no trade |
| Entering without checking linking account | Could be a manufactured narrative |

---

## Score History

| Coin | Narrative Score | BC Score | Migration Score | Outcome |
|------|----------------|----------|-----------------|---------|
| embers | 6/6 | 3/3 | 5/5 | ✅ Winner |

---

## Related Pages

- [[patterns/narrative-triggers]]
- [[patterns/winner-checklist]]
- [[patterns/migration-signals]]
- [[playbooks/migration-alert]]
- [[coins/embers]]
- [[coins/coin-index]]
