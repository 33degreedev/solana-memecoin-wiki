---
name: Narrative Triggers — Pattern Library
type: pattern
tags: [pattern, signal]
---

# Narrative Triggers — Pattern Library

> **Data confidence: LOW** — Based on 1 confirmed case study (embers). Taxonomy is logical but unvalidated. Add cases as they're studied.

What kinds of narratives make memecoins move? This page catalogs narrative types, ranks their typical strength, and shows confirmed examples.

---

## Narrative Tier List

| Tier | Type | Typical Strength | Example |
|------|------|-----------------|---------|
| S | CEO / founder name drop (exact word) | Extreme | embers — Sam Altman tweets "embers" |
| S | Official product name by known entity | Extreme | — (no case study yet) |
| A | AI company milestone + naming | Very high | embers (GPT-5.5 TikZ unicorn) |
| A | Political figure live speech / slogan | Very high | AIB — Trump "America Is Back" |
| A | Major celebrity engagement | Very high | — |
| A | Video-embedded name (exec/builder, spoken in video) | Very high | chloe — Nikita Bier pig name in video |
| B | Credible crypto influencer frames narrative | High | @xacrypto1 → embers |
| B | News event + matching token name | High | AIB (RT tweet, 3.51M followers) |
| C | Community meme + virality | Medium | — |
| C | Token name matches trending topic | Medium | — |
| D | Dev-manufactured narrative (no external hook) | Low | — |
| F | Anonymous claim, no verifiable source | Very low | — |

> ⚠️ **Political figure narratives attract more vamping.** High-profile political triggers (Trump, Elon political statements) generate multiple competing coins faster than AI/tech triggers. Add vamping check before entering any coin from a Tier A political narrative. See [[patterns/vamping]].

---

## Narrative Quality Scoring

Score any incoming narrative on these 6 dimensions. **4+ = investigate on-chain. 6/6 = high conviction.**

| Dimension | 0 pts | 1 pt |
|-----------|-------|------|
| Source credibility | Unknown / anonymous | Verifiable public figure |
| Source reach | < 100K followers | 1M+ followers (CEO, celebrity) |
| Name alignment | Loose interpretation | Token name = exact word from source |
| Organic origin | Manufactured / planned | Unsolicited real event |
| Simplicity | Needs explanation | 1 sentence, anyone understands |
| Lore depth | No backstory | Mythology, meaning, cultural resonance |

**embers score: 6/6** — Sam Altman (verifiable + 35M+ followers), exact word "embers", organic GPT-5.5 post, "ChatGPT mascot" is 3 words, Merriam-Webster definition provides lore.

---

## Confirmed Cases

### AIB (America Is Back) — Apr 23, 2026 ✅ WINNER (Bonk vamp) / ❌ DEAD (pump.fun original)

**Narrative:** RT (@RT_com, 3.51M) tweeted Trump's live speech where he called "America Is Back" his new political slogan. Three AIB tokens launched simultaneously — a vamping scenario.

**Score:** 5/6
**BC fill time:** ~1–2 minutes (extremely fast — political figure narratives = immediate bot response)
**Key finding:** Platform alignment determined the winner. Bonk AIB (Trump = Bonk infrastructure) beat pump.fun AIB (first mover) decisively — $658K ATH vs $251K, $2.8M vs $1.7M volume, still alive vs dead.

→ Full analysis: [[coins/aib-america-is-back]]
→ Vamping framework: [[patterns/vamping]]

---

### chloe (2ra5Id...pump) — Apr 23, 2026 ✅ WINNER

**Narrative:** Nikita Bier (@nikitabier, ~1M followers — head of product @X, advisor @Solana) tweeted a video of a boar delivered to his office to celebrate hitting 1M followers. Someone in the video says the pig's name: **"Chloe."** Token launched on pump.fun with that name.

**Score:** 5/6 (no lore depth — pig name, no mythology)
**Volume:** $5.56M (single coin — no vamping)
**ATH MC:** ~$1.68M
**New pattern:** Video-embedded trigger — name was spoken in video, not in tweet text. Bots can't parse audio; slower propagation creates wider entry window.
**Key insight:** Solana advisor status amplified credibility beyond raw follower count.

→ Full analysis: [[coins/chloe]]

---

### embers (C4b1rL9g) — Apr 23, 2026 ✅ WINNER

**Narrative:** Sam Altman tweeted "embers" in response to an OpenAI researcher's GPT-5.5 TikZ unicorn post. Token launched 13 seconds after the tweet. @xacrypto1 framed it as "ChatGPT mascot."

**Score:** 6/6
**BC fill time:** 23 minutes
**Key signal:** 16 sniper wallets in 2 seconds = automated systems watching Sam Altman's replies

→ Full analysis: [[coins/embers]]

---

## Narrative Types — Deep Dive

### Type 1: CEO / Founder Name Drop

**What it is:** A founder or CEO of a major AI or crypto company uses a specific word or phrase in a tweet. Someone launches a token with that exact name within minutes.

**Why it works:**
- Provides instant credibility by association
- Token name = CEO's word = no interpretation gap
- Degens can explain it in 5 words ("Sam Altman named it")
- Bots monitor high-follower accounts and trigger automatically

**Watch for:** Sam Altman (@sama), Elon Musk, Vitalik Buterin, Brian Armstrong, CZ. Any single evocative word in a reply to AI/crypto content.

**Speed required:** < 5 minutes from tweet to entry. The window closes fast.

---

### Type 2: AI Milestone + Naming

**What it is:** A new AI capability is demonstrated publicly. The model, image, or artifact produced gets named and that name becomes the token.

**Why it works:**
- AI news has broad reach and generates genuine excitement
- The "naming" moment feels authentic, not financial
- Visual content (generated art, video) spreads faster than text

**Example:** GPT-5.5 TikZ unicorn → "embers" was the name Altman gave it.

---

### Type 3: Video-Embedded Name

**What it is:** A high-credibility account posts a video where a name is spoken or shown visually (a pet, person, place, object). Someone launches a token with that name. The tweet text itself contains no obvious coin name.

**Why it works:**
- Requires watching/listening — human discovery, not bot parsing
- Propagation is CT reply-chain driven ("did anyone catch the pig's name?")
- Slower spread = wider entry window than text-based triggers
- Milestone/celebratory videos have outsized engagement (higher share rate)

**Edge for fast traders:**
- If you watch the video before CT reply chains amplify the name — you are early
- BC will be at 0–10% filled while others are still debating what the name was
- Vamping is rare — the name is unambiguous (proper name), no platform argument possible

**Chloe case:** Nikita Bier's pig named "Chloe" in a 1M-follower celebration video. $5.56M volume, $1.68M ATH. No vamping. The entire edge was spotting the name in the video before CT reply chains surfaced it.

**Watch for:** Any video tweet from a figure with 500K+ followers where the tweet text doesn't contain an obvious coin name. Watch the first 30 seconds of any attached video.

---

### Type 3: Credible Crypto Figure Frames the Narrative

**What it is:** A known crypto account (50K+ followers, respected reputation) links a token address to an existing viral tweet and articulates the thesis.

**Why it works:**
- Does the "translation" work for degens who saw the tweet but didn't connect it to crypto
- Creates a quotable thesis ("ChatGPT mascot")
- The framing account's credibility lends legitimacy

**Watch for:** Accounts tagged as "quant", "on-chain analyst", "defi researcher". Track accounts that have done this successfully before.

---

## Red Flags: Narratives That Fail

| Red Flag | Why |
|----------|-----|
| Token name is an interpretation, not exact words | "spirit of the unicorn" ≠ "embers" — ambiguity kills |
| CEO tweet is older than 30 min before token launch | Window closed, snipers already in |
| Linking account is newly created (<30 days old) | Manufactured narrative, not organic discovery |
| The "CEO" has <1M followers | Not enough reach to generate BC-filling volume |
| Narrative requires 3+ sentences to explain | Won't spread in meme format |
| Bonding curve is already >40% filled when you see it | You missed the move |

---

## How to Monitor for Narrative Triggers

**Manual method:**
1. Follow @sama, high-follower AI researchers, crypto founders on Twitter
2. Filter notifications for replies and quote tweets
3. When a single evocative word appears in a reply → check pump.fun immediately for matching tokens
4. If found and recently launched → check on-chain signals (see [[patterns/winner-checklist]])

**Signal stack for highest-conviction entry:**
1. Narrative tier S or A
2. Narrative score 5–6/6
3. Token launched < 10 min ago
4. BC < 30% filled
5. On-chain signals pass [[patterns/winner-checklist]]

---

## Related Pages

- [[coins/coin-index]]
- [[patterns/winner-checklist]]
- [[patterns/migration-signals]]
- [[patterns/volume-fingerprints]]
- [[playbooks/narrative-trade]]
