---
title: "HOME — Solana Is Home (Apr 24, 2026)"
name: HOME — Solana Is Home (Apr 24, 2026)
description: Breakdown of the HOME token EXTREME migration. @solana official tweet catalyst, 17-second BC fill, 18,802 SOL raised, west + jijo in BC.
type: case_study
status: complete
tags: [EXTREME, catalyst, official-account, narrative, tweet-driven]
---

# HOME — Solana Is Home | Case Study

**Date:** 2026-04-24
**CA:** `CT2khHUinJi4Rsa7n7Ft7DRWCprV9ZFKEo5pTBCwpump`
**BC Pool:** `ARnoHoAfJ8kV87F5XCgz1aBNubiuhMiTN7DwMCXBAZqu`
**Migration tier:** EXTREME (17 seconds)

---

## Catalyst

**Apr 21:** @smsonx tweeted a hand-drawn house with the Solana logo:
> "Wherever I go, @solana is always home."

toly (Anatoly Yakovenko, Solana co-founder) liked the tweet.

**Apr 24, 14:16 PDT (21:16 UTC):** @solana official account replied:
> "home sweet Solana"

That single reply — from the @solana official account, not just an influencer — was the ignition signal. A token matching the narrative launched within ~60 seconds.

---

## Migration Breakdown

| Field | Value |
|---|---|
| Token created | 21:17:06 UTC |
| Token migrated | 21:17:23 UTC |
| BC duration | **17 seconds** |
| Tier | **EXTREME** |
| Total SOL raised in BC | **~217 SOL** (~$18,802 USD @ ~$86.57/SOL) |
| Total BC transactions (rows) | 614 |
| First buyer block | 1777065426 |
| Migration block | 1777065443 |

The entire bonding curve filled in 17 seconds. All buys happened within a single block range. This is one of the fastest BC fills observable — faster than most bots can react to a standard migration event.

---

## Known Traders in BC

Both confirmed in BC during the 17-second window:

| Trader | SOL In | USD Value | Txns | Notes |
|---|---|---|---|---|
| **west** | ~17.78 SOL | ~$1,539 | 9 | Largest single wallet in BC |
| **jijo** | ~110 SOL | TBD | 2 | (USD value not calculated) |

west's 9 BC transactions in 17 seconds = west was scripted / pre-positioned. Not a manual click — this is automated execution reacting to the @solana tweet.

---

## Top BC Buyers (All Wallets)

| Rank | Wallet | SOL In |
|---|---|---|
| 1 | west (`JDd3hy3...`) | 17.78 |
| 2 | `57stAMF...` | 6.91 |
| 3 | `CyaE1Vx...` | 6.36 |
| 4 | `CDjiKpq...` | 5.99 |
| 5 | `7EmUSAXb...` | 5.87 |
| 6–10 | Various | ~5–6 SOL each |

The top wallets each put in 5–18 SOL within 17 seconds. Total BC filled at ~217 SOL (~$18,802 USD @ ~$86.57/SOL). Bot-level execution — no manual buyer could react in this window.

---

## Why the Detector Missed It

**Root cause: bot was restarted at 14:24 PDT. Migration was at 14:17 PDT — 7 minutes earlier.**

The migration happened while the detector was being restarted to add new wallets (west, jijo, etc. — those wallets were added in the same session). Classic timing failure.

Secondary cause: even with the bot running, PumpPortal may not have delivered the migration event (observed earlier with the `EGEzijzWJTdjQ9Y9` token — migration event was missing but account trade events arrived). The missed-migration recovery fix was deployed after this miss.

---

## Lessons

### 1. Watch @solana official account like a launchpad trigger
When @solana (or toly directly) engages with a narrative — especially an image-based tweet with emotional resonance — a token will be created within minutes. The gap between tweet and launch is usually 30–120 seconds. There is no time to be slow.

**Action:** Add @solana, @toly, @aeyakovenko as Twitter alert triggers. When they tweet/engage with narrative content, prepare to ape immediately.

### 2. EXTREME tiers are bot battles, not human trades
17 seconds. 18,802 SOL. 9 west transactions. No human clicked fast enough to get early. The only winning strategy on EXTREME tiers is pre-positioning or sub-second automated execution.

**Action:** For EXTREME migrations, the detector alert is for awareness and post-migration momentum trading — not for getting in at BC prices. The BC is already over.

### 3. Known traders in BC = confirmation signal even post-migration
west was in with 17.78 SOL (~$1,539 USD) — the largest single BC buyer. Even if you missed the BC entirely, seeing that west was in is a strong signal to buy the post-migration dip immediately.

**Action:** On EXTREME migrations, the alert should explicitly surface BC trader sizes — not just names. "west: 17.78 SOL in BC" is a much stronger call than "west: in BC."

### 4. Don't restart the bot during active trading hours
The bot restart at 14:24 to add wallets caused the miss. Config changes should be batched for off-hours (early morning US, late night UTC).

**Action:** Queue wallet additions and restart at ~08:00 UTC when pump.fun activity is lowest.

### 5. Official account narratives move faster than influencer narratives
@smsonx tweet (Apr 21) → toly like → no token. @solana replies (Apr 24) → token within 60s. The trigger was the **official account engagement**, not the original tweet. Influencer tweets give minutes. Official account engagement gives seconds.

---

## Signal Pattern

```
[Official account engages narrative tweet]
  → Token launches within 60s
    → BC fills in <30s (EXTREME)
      → Known traders bot-buying 100-1500 SOL each
        → Migration
          → Post-migration: MC at $50K+, momentum buyers pile in
```

This pattern (official account → EXTREME migration → bot whale buyers) is repeatable whenever there's a strong visual/emotional narrative that gains official Solana backing.

---

## Related

- [[frameworks/migration-detector-architecture]] — system architecture for catching these events
- west — wallet analysis (page not yet created)
- [[coins/aib-america-is-back]] — another narrative-driven EXTREME migration
- [[frameworks/data-extraction-proposals]] — how to monitor for Twitter catalyst signals
