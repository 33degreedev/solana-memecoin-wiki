---
title: "Jijo — Trader Profile"
name: Jijo — Trader Profile
type: trader-profile
tags: [trader, wallet-analysis]
---

# Jijo — Trader Profile

**Data as of:** Apr 22, 2026 (8-day sample, 160 tokens)
**Assessment:** ✅ Real skill — 68% win rate confirmed
**Farmer detection score:** 0/5 (not assessed formally — win rate consistent with longer holds)

---

## Performance

| Metric | Value | Source |
|--------|-------|--------|
| Win rate | **68.2%** | axiom_trades_apr22 (160 tokens) |
| GMGN win rate | 68.37% | GMGN (confirms data) |
| Profitable positions | 107 / 157 | axiom_trades_apr22 |
| Losses | 50 / 157 | axiom_trades_apr22 |

---

## Trading Style

| Factor | Value |
|--------|-------|
| Entry size | $100–$500 (avg $233, median $108) |
| Hold time | 65% < 5 min, mode 3–5 min |
| Peak hours | 13:00–22:59 UTC (US daytime) |
| Multi-entry rate | 77.5% of tokens (scales into winners) |
| Trades per day | ~20 |
| Token age at entry | 2–10 minutes (earlier than theo) |

### Entry Logic
Jijo enters very new tokens (2–10 min) appearing on Birdeye trending with fast growing volume ($100k–$1M liquidity, 50+ new holders/min, +20%+ from launch). First entry is small ($100); if price moves, scales in ($300 more). If not, cuts and moves on.

### Exit Logic
Holds 3–30 minutes depending on momentum. No rigid timer — exits when momentum peaks or at a mental stop. This is less mechanical than theo's system and requires more judgment.

### What Makes Jijo's 68% Win Rate Real
- Longer hold time (3–30 min) vs theo (30–60s) means more price discovery happens before exit
- Higher win rate but lower frequency than theo
- Daily → monthly consistency: 68% stable across both timeframes (no farming jump)

---

## Discipline Assessment

| Trait | Assessment |
|-------|-----------|
| Entry timing | ✅ Consistent 2–10 min window |
| Scaling strategy | ✅ Test entry → confirm → scale |
| Position sizing | ✅ $100 test, $300 add on confirmation |
| Hold discipline | ⚠️ Mental stop, not mechanical — harder to replicate |
| Hours discipline | ✅ Only trades peak hours (13–23 UTC) |

---

## How to Front-Run

**The opportunity:** Jijo enters 2–10 minutes after launch. If you enter 1–2 minutes earlier:
- Your entry: $0.0001
- Jijo enters at $0.00012 (2 min later, +20% already)
- Price pumps to $0.0002 when jijo buying hits
- You exit at 2× while jijo exits at 1.67×

**Signals that predict jijo's entry:**
- Token on Birdeye trending, 2–10 min old
- Volume growing fast ($200K+ in last 5 min)
- Liquidity $100K–$1M
- Holders growing 50+/min
- Price +20%+ from launch

**Warning:** Front-running jijo requires speed and consistent monitoring. Recommended to master theo's system first before attempting jijo-style front-runs.

See [[playbooks/theo-style]] for the actionable guide (includes jijo comparison).

---

## Peak Hours vs Theo

| Trader | Peak Hours (UTC) | US Equivalent |
|--------|-----------------|---------------|
| Jijo | 13:00–22:59 | 8am–5pm EST |
| Theo | 17:00–23:59 | 12pm–6pm EST |
| Overlap | 17:00–22:59 | 12pm–5pm EST |

The 17:00–22:59 window is when both trade — highest signal density for front-running strategies.

---

## Sources

- `axiom_trades_apr22.txt` (8-day sample, 160 tokens)
- `kol_scan_leaderboard_apr22.txt`
- GMGN trader profile

---

## Related Pages

- [[traders/theo]]
- [[traders/cented]]
- [[playbooks/theo-style]]
- [[frameworks/farmer-detection]]
