---
title: "Data Extraction Proposals: Reddit & X for Quality Wallet Discovery"
name: "Data Extraction Proposals: Reddit & X for Quality Wallet Discovery"
type: framework
tags: [framework, system-design]
---

# Data Extraction Proposals: Reddit & X for Quality Wallet Discovery

## Executive Summary

These 8 proposals outline concrete, actionable methods to extract high-quality trading data from Reddit and X (Twitter) to identify profitable wallets, validate traders, and build your knowledge base systematically. Each proposal includes specific data sources, extraction methods, and how to add findings to your wiki.

---

## **PROPOSAL 1: Reddit Subreddit Sentiment Tracking**

### 📍 Sources

- r/solana
- r/SolanaMemecoins
- r/SolanaTrading
- r/degentraders
- r/cryptocurrency

### 🔍 What to Extract

1. **Wallet addresses mentioned in posts** (format: `/extract_wallets`)
2. **Sentiment around specific tokens** (bullish/bearish/neutral)
3. **Trader recommendations** (who people trust)
4. **Post engagement** (upvotes = validation signal)

### 📊 Data Format to Store

```
---
source: Reddit
subreddit: r/solana
post_title: "This trader theo just hit #2 on KOL"
wallet_mentioned: [wallet_address_here]
sentiment: Bullish
upvotes: 245
comments: 89
date: 2026-04-22
---
```

### 🛠️ How to Execute

1. **Manual daily check**: Spend 15 min/day scanning top r/solana posts
2. **Search keywords**: "wallet", "address", "trading", "profitable"
3. **Record findings** in `/raw/reddit_sentiment_apr22.txt`
4. **Monthly update**: Create analysis page: `Reddit_Community_Validation.md`

### 📈 What You'll Learn

- Which traders are discussed most (validation signal)
- Which tokens are getting attention pre-pump (early signal)
- Red flags (scams mentioned repeatedly)
- Emerging traders before leaderboards show them

### ⏱️ Time Investment

- 15 min/day = ~100 min/month
- 1 page per month

---

## **PROPOSAL 2: X/Twitter Wallet Tracking via Influencer Bio Links**

### 📍 Sources

- Solana influencer bios (look for wallet addresses)
- Twitter threads about "my wallet is..."
- Linked blogs/websites with disclosed addresses
- @gmgn_ai mentions (they publish wallet lists)

### 🔍 What to Extract

1. **Influencer name → wallet address mapping**
2. **Bio changes** (when influencers update their wallets = strategy shift)
3. **Linked wallet addresses from threads**
4. **@mentioned wallets** in popular traders' tweets

### 📊 Data Format to Store

```
---
source: Twitter
influencer: @TheoProfessor
wallet_address: [address]
bio: "Solana trader, 55% win rate"
followers: 12500
verified: Yes
latest_mention_date: 2026-04-22
---
```

### 🛠️ How to Execute

1. **Identify 20-30 solana traders on Twitter** (start with KOL leaders)
2. **Screenshot their bios** (record wallet if listed)
3. **Search their tweets for wallet mentions**
4. **Cross-reference with GMGN/Nansen data**
5. **Store in `/raw/twitter_influencer_wallets_apr22.txt`**

### 📈 What You'll Learn

- Direct wallet-to-influencer mapping
- Which traders are transparent (good sign)
- Wallet changes over time (evolution tracking)
- Influencer network (who follows who)

### ⏱️ Time Investment

- 1 hour initial research
- 30 min/week maintenance

---

## **PROPOSAL 3: GMGN.ai Top Wallets Export + Analysis**

### 📍 Source

GMGN.Ai focuses on tracking profitable wallets and known high performing traders within the Solana ecosystem. The platform labels wallets such as top snipers or key opinion leaders and provides Telegram alerts when those wallets enter or exit positions.

### 🔍 What to Extract

1. **Top 50 GMGN wallets** (daily snapshot)
2. **Win rates, PnL, trade count**
3. **Wallet labels** (sniper, KOL, whale, etc.)
4. **Movement history** (who's rising/falling)

### 📊 Data Format to Store

```
---
source: GMGN.ai
date: 2026-04-22
top_wallet: [address]
pnl_30d: +1707.11
win_rate: 55.9%
label: KOL
rank_change: Up from #25
trades: 1312
---
```

### 🛠️ How to Execute

1. **Visit gmgn.ai daily** (takes 5 min)
2. **Screenshot top 50 wallets** with metrics
3. **Export as CSV or text**
4. **Store in `/raw/gmgn_top_wallets_apr22.txt`**
5. **Weekly comparison**: Which wallets stayed top 10?

### 📈 What You'll Learn

- Real-time ranking shifts
- Emerging talent (wallets moving up fast)
- Sustainable vs. lucky traders (consistency)
- Wallet labels validation (are snipers actually profitable?)

### ⏱️ Time Investment

- 5 min/day = ~35 min/month
- Automated if using API

---

## **PROPOSAL 4: Twitter Trader Comparison Thread Analysis**

### 📍 Source

- "Compare [Trader A] vs [Trader B]" threads
- "Who to follow?" discussion threads
- "Best solana traders 2026" threads
- Retweet chains of trader discussions

### 🔍 What to Extract

1. **Trader comparisons** (who wins in community debate?)
2. **Reasons given** (why follow X over Y?)
3. **Red flags mentioned** (scam reports, farming accusations)
4. **Upvote/like distribution** (consensus validation)

### 📊 Data Format to Store

```
---
source: Twitter Thread
thread_title: "Best Solana traders 2026"
date: 2026-04-22
mentions:
  - theo (mentioned 47 times, 89% positive)
  - cented (mentioned 34 times, 12% positive - farming accusations)
  - radiance (mentioned 23 times, 96% positive)
red_flags_mentioned:
  - "Cented farms copy traders"
  - "theo's edge is real"
consensus: theo > radiance > cented
---
```

### 🛠️ How to Execute

1. **Search Twitter**: "best solana traders", "who to follow solana"
2. **Read top 10 threads** per week
3. **Tally mentions** (who gets talked about most?)
4. **Note sentiment** (positive vs negative)
5. **Store in `/raw/twitter_trader_comparison_apr22.txt`**

### 📈 What You'll Learn

- Community consensus on trader quality
- Real-time sentiment shifts
- Accusations/red flags being discussed
- Emerging traders gaining buzz

### ⏱️ Time Investment

- 30 min/week

---

## **PROPOSAL 5: X Thread Mining for Wallet Addresses (Advanced)**

### 📍 Source

- Solana trading threads with embedded wallet addresses
- "Check my wallet:" posts
- Proof-of-trade threads (screenshot showing address)
- GMGN/Nansen linked thread discussions

### 🔍 What to Extract

1. **Wallet addresses from screenshots**
2. **Performance claims** (what they claim vs reality)
3. **Community validation** (do people verify the wallet?)
4. **Timestamp** (when was this posted?)

### 📊 Data Format to Store

```
---
source: Twitter
thread_author: @Unknown_Trader
claim: "Made +500 SOL in 30 days"
wallet_address: [address_from_screenshot]
wallet_verified: Yes/No
community_response: Verified in replies, 23 confirmations
date: 2026-04-22
---
```

### 🛠️ How to Execute

1. **Search Twitter**: "[wallet address]" solana, "proof of trade", "check my holdings"
2. **Screenshot threads with wallet addresses**
3. **Cross-verify wallets on Solscan/GMGN**
4. **Check if claims match reality**
5. **Store findings in `/raw/twitter_wallet_claims_apr22.txt`**

### 📈 What You'll Learn

- Traders who are transparent (sharing wallets publicly)
- Claims vs reality (who's honest vs lying)
- Emerging talent (unknown wallets with real performance)
- Fraud detection (impossible claims)

### ⏱️ Time Investment

- 1 hour/week

---

## **PROPOSAL 6: Reddit Comment Scraping for Wallet Mentions**

### 📍 Source

- r/solana comments (deep dives)
- r/SolanaMemecoins discussion threads
- r/degentraders case studies
- Comment threads on trader discussion posts

### 🔍 What to Extract

1. **Wallet mentions in comments**
2. **Discussion context** (why is this wallet mentioned?)
3. **Validation** (do other users confirm/deny?)
4. **Hidden gems** (wallets mentioned by 1-2 people, not in leaderboards yet)

### 📊 Data Format to Store

```
---
source: Reddit Comment
subreddit: r/SolanaMemecoins
post_title: "Which traders are you copying?"
commenter_karma: 1200
wallet_mentioned: [address]
context: "This wallet theo is insane, 55% win rate sustained"
validation: 12 replies confirming, 1 reply questioning
date: 2026-04-22
---
```

### 🛠️ How to Execute

1. **Subscribe to r/solana and r/SolanaMemecoins**
2. **Weekly deep dive**: Read top 5 discussion threads
3. **Extract comments mentioning wallets**
4. **Note commenter reputation** (karma, history)
5. **Store in `/raw/reddit_comments_wallets_apr22.txt`**

### 📈 What You'll Learn

- Early validators of traders (people who found them first)
- Community conversations about specific strategies
- Hidden wallets (not yet on leaderboards)
- Red flags from informed community members

### ⏱️ Time Investment

- 1 hour/week

---

## **PROPOSAL 7: Twitter Sentiment API (Semi-Automated)**

### 📍 Source

- Solana token sniper fetching twitter account posts - bots monitor a specific Twitter account for new tweets containing Solana token addresses or pair tokens.
- X API v2 (paid, but powerful)
- Apify web scraping platform (free tier)

### 🔍 What to Extract

1. **Real-time tweets** mentioning specific traders (theo, radiance, etc.)
2. **Sentiment analysis** (positive/negative/neutral mentions)
3. **Engagement metrics** (retweets, likes, replies)
4. **Time-series data** (sentiment over days/weeks)

### 📊 Data Format to Store

```
---
source: Twitter API
keyword: "theo solana trader"
date: 2026-04-22
tweets_found: 147
sentiment_breakdown:
  positive: 128 (87%)
  negative: 12 (8%)
  neutral: 7 (5%)
avg_engagement: 234 likes per tweet
trend: Sentiment increasing over past 7 days
---
```

### 🛠️ How to Execute

**Option A (Manual - Free):**

1. Search Twitter for "theo solana", "radiance solana", etc.
2. Screenshot trending results
3. Manually count sentiment
4. Store in `/raw/twitter_sentiment_apr22.txt`

**Option B (Semi-Automated - $10-50):**

1. Use Apify scraper (Python script)
2. Extract tweets + engagement metrics
3. Basic sentiment tagging (positive/negative keywords)
4. Export to CSV
5. Store in `/raw/twitter_sentiment_automated_apr22.csv`

### 📈 What You'll Learn

- Real-time community sentiment shifts
- When traders gain/lose trust
- Emerging scandals (negative sentiment spike)
- Trader reputation trends

### ⏱️ Time Investment

- 30 min/week (manual)
- 5 min/week (automated, if set up)

---

## **PROPOSAL 8: Cross-Platform Wallet Validation (The Power Combo)**

### 📍 Source

Combine all previous proposals:

- Reddit mentions
- Twitter influencer wallets
- GMGN top wallets
- Wallet address threads
- Sentiment data

### 🔍 What to Extract

Create a **master validation matrix**:

|Wallet|Found on|KOL Status|Reddit Mentions|Twitter Sentiment|GMGN Rank|Validation Score|
|---|---|---|---|---|---|---|
|theo|Twitter bio + Reddit|KOL (labeled)|12 positive|87% positive|#2|✅ 9/10|
|radiance|GMGN|Whale|8 positive|92% positive|#20|✅ 8/10|
|cented|Twitter + GMGN|KOL|34 mixed|12% positive|#1|⚠️ 3/10|

### 📊 Data Format to Store

```
---
wallet_address: [theo's address]
validation_sources:
  - Twitter influencer bio: Confirmed
  - GMGN labeling: KOL
  - Reddit mentions: 12 (all positive)
  - Sentiment: 87% positive
  - Monthly leaderboard: #2
  - Farmer detection flags: 0/5
  - Consistency: Daily #9 → Monthly #2 ✅

trust_score: 9/10
recommendation: SAFE TO COPY ✅
---
```

### 🛠️ How to Execute

1. **Build master wallet list** from Proposals 1-7
2. **Cross-validate each wallet** across all sources
3. **Score each wallet** (0-10 scale)
4. **Create wiki page**: `Master_Wallet_Validation.md`
5. **Update monthly** with new data

### 📈 What You'll Learn

- Which sources are most reliable?
- Perfect confidence signal (validated on 5+ sources)
- Red flags (scattered mentions, mixed sentiment)
- Emerging vs proven traders

### ⏱️ Time Investment

- 2 hours/month (combining all proposals)
- Results: Bulletproof trader evaluation

---

## **Implementation Roadmap**

### Week 1: Foundation

- ✅ Proposal 3 (GMGN.ai snapshot - fastest ROI)
- ✅ Proposal 2 (Twitter influencer bios - easy)

### Week 2-3: Expand

- ✅ Proposal 1 (Reddit subreddit tracking)
- ✅ Proposal 4 (Twitter comparison threads)

### Week 4: Validate

- ✅ Proposal 5 (Wallet address extraction)
- ✅ Proposal 6 (Reddit comment mining)

### Month 2: Scale

- ✅ Proposal 7 (Twitter sentiment API)
- ✅ Proposal 8 (Master validation matrix)

---

## **How to Add to Your Wiki**

For each proposal completed:

1. **Create `/raw/[proposal_name]_apr22.txt`** with extracted data
2. **Create wiki page** (example: `Reddit_Sentiment_Analysis.md`)
3. **Follow CLAUDE.md rules:**
    - Cite all sources
    - Document methodology
    - Flag uncertainty
    - Cross-link related pages

### Example Wiki Page Structure

```markdown
# [Proposal Name] Analysis

## Data Collection Method
[Explain how you extracted the data]

## Findings
[What you discovered]

## Top Wallets/Traders Identified
[Ranked list with validation]

## Red Flags Detected
[Suspicious activity]

## Sources
- /raw/proposal_name_apr22.txt

## Related Pages
- [[frameworks/farmer-detection]]
- [[traders/theo]]
- [[frameworks/position-sizing]]
```

---

## **Expected Output: After All 8 Proposals**

### What You'll Have Built:

1. ✅ **List of 50+ validated Solana traders**
2. ✅ **Wallet-to-influencer mapping**
3. ✅ **Community sentiment trends**
4. ✅ **Red flag detection system**
5. ✅ **Monthly leaderboard alternative** (Reddit-powered)
6. ✅ **Early warning system** (detect farming before leaderboards do)
7. ✅ **Hidden gems database** (quality traders not on top 10 yet)

### What This Enables:

- 🎯 **Copy traders with community validation**
- 🎯 **Avoid farmers before they collapse**
- 🎯 **Find emerging talent early**
- 🎯 **Real-time sentiment alerts**
- 🎯 **200+ hours of manual work, automated into 10 minutes/week**

---

## **Success Metrics**

Track these quarterly:

|Metric|Goal|
|---|---|
|Validated wallets identified|50+|
|Accuracy of farmer detection|90%+|
|Time to identify new talent|<1 week vs 4+ weeks|
|Community sentiment correlation|85%+|
|Cross-platform confirmation rate|75%+|

---

## **Tools Required (All Free or Low-Cost)**

- GMGN.ai (free tier)
- Twitter/X (free)
- Reddit (free)
- Solscan (free)
- Apify (free tier for scraping, optional)
- Obsidian (free for local use)

---

## **Next Step**

Pick **Proposal 3 (GMGN.ai)** or **Proposal 2 (Twitter influencers)** — whichever takes 1 hour and do it TODAY.

Then add findings to `/raw/` and create a wiki page.

This will compound into a **complete alternative leaderboard** that's better than any platform because it includes community validation, sentiment, and farmer detection.

---

## **Sources**

- GMGN.Ai documentation on tracking profitable wallets
- Solana wallet tracking via Twitter monitoring
- Influencer wallet discovery methods via blockchain explorers

## Related

- [[frameworks/farmer-detection]] — Detect suspicious traders before copying
- [[frameworks/trade-deconstruction]] — Reverse-engineer trader strategies from data
- [[traders/theo]] — Example of data-validated trader
- [[playbooks/theo-style]] — How to operationalize validated trader patterns