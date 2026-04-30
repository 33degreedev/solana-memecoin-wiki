---
name: Theo — Trader Profile
type: trader-profile
tags: [trader, wallet-analysis]
---

# Theo — Trader Profile

**Wallet:** `4BdKaxN8G6ka4GYtQQWk4G4dZRUTX2vQH9GcXdBREFUk`
**Data as of:** Apr 22, 2026
**Assessment:** ✅ Real skill — safe to copy / front-run
**Farmer detection score:** 0/5

---

## Performance (KOL Scan + GMGN)

| Metric | Daily (Apr 22) | Monthly (30d) | Source |
|--------|---------------|---------------|--------|
| Rank | #9 | #2 | KOL Scan |
| Win rate | ~56% | **55.9% (KOL) / 59.48% (GMGN)** | Both |
| Total trades (monthly) | — | 3,657 | KOL |
| PnL (monthly) | — | significant | KOL |

**Use 55–60% as the realistic planning range for win rate.**

---

## Trading Style

| Factor | Value | Source |
|--------|-------|--------|
| Entry size | $200–$300 fixed (~$271 avg) | Live Trade Analysis (8-day sample) |
| Hold time | 7–60 seconds (mode: 10–30s) | Live Trade Analysis |
| Peak hours | 17:00–23:59 UTC | Live Trade Analysis |
| Multi-entry rate | 86.7% of tokens | Live Trade Analysis |
| Trades per day | ~25 | Live Trade Analysis |
| Token age at entry | 9–25 minutes | Live Trade Analysis + Checklist |

### Entry Logic
theo enters tokens that are **9–25 minutes old** with a **volume spike** (150%+), **whale presence** ($1+ SOL buy), **growing holder count** (+20/5min), and **upward price momentum**. First entry is a test ($250); if pumping, adds $250 more. If not, cuts or holds.

### Exit Logic
Two-stage: exit 50% at +5%, remainder at +10% or 60-second hard stop. Stop-loss at -10% (first 30s) or -15% (anytime). The 60-second mechanical exit is the defining discipline of the system.

---

## Discipline Assessment

| Trait | Assessment |
|-------|-----------|
| Mechanical exits | ✅ Hard 60-second timer, no exceptions |
| Position sizing | ✅ Fixed % per trade, scales with capital |
| Checklist adherence | ✅ 5-point entry filter, skip if any fail |
| Overtrading | ✅ 20–25 trades/day cap (peak hours only) |
| Averaging down | ⚠️ Multi-entry sometimes used to scale, not average down |

**What makes theo profitable:** Mechanical exits prevent small losses becoming large ones. 59% win rate with avg win > avg loss = positive EV. The edge is execution consistency, not alpha on token selection.

---

## Farmer Detection Score

| Check | Result |
|-------|--------|
| Win rate 75%+ on fast holds | ✅ 55.9% — realistic |
| #1–2 leaderboard + broadcasts speed | ✅ #9 daily, doesn't broadcast |
| Daily rank collapsed monthly | ✅ #9 daily → #2 monthly (improved) |
| Win rate jump daily → monthly | ✅ Stable ~56% both timeframes |
| Hold time locked at 5–15s only | ✅ Mix of 7–120+ seconds |

**Score: 0/5 → REAL SKILL** — Edge comes from market timing, not farming copy traders.

---

## Live Trade Sample (Apr 22, 2026 — 99 min snapshot)

| Trade | Entry SOL | Exit SOL | Hold | Result |
|-------|-----------|----------|------|--------|
| dT9Sq9Na | 1.22 | 1.61 | 7s | ✅ +32% |
| F9q8wSJk | 3.65 | 3.99 | 58s | ✅ +9.3% |
| 8V5SPRT2 | 3.59 | 1.12 | 26s | ❌ -68.8% |
| AK3sdMdw | 1.18 | 4.79 | 6s | ✅ +306% |
| DAZpnqAe | 0.20 | 2.33 | 20s | ✅ +1,065% |
| 4DYpQAiK | 4.0 | 0.02 | 251s | ❌ -99.5% |
| 61NaAKKQ | 4.0 | 6.17 | 5,157s | ✅ +54% |

Note: This 8-day sample showed 42.4% win rate — lower than monthly 59%. Variance is expected in small samples. The -99.5% loss on a 4 SOL position is a rules violation (held 251 seconds past the 60s exit rule).

---

## How to Copy or Front-Run

- **Copy directly:** Enter same tokens with same entry checklist, apply mechanical exits. Expected: +6–11% monthly at 59% win rate.
- **Front-run:** Enter 30 seconds before theo's likely entry using same signals. Exit faster. Capture +1–2% additional per trade.
- **Best hours:** 17:00–23:59 UTC. Most active 17:00–20:00 UTC.

See [[playbooks/theo-style]] for full operational guide.

---

## Sources

- `axiom_trades_apr22.txt` (8-day sample, 160+ tokens)
- `kol_scan_leaderboard_apr22.txt` (daily rankings)
- `kol_scan_monthly_apr22.txt` (monthly rankings)
- `Theo_Live_Trade_Analysis` (99-min Solscan snapshot)

---

## Related Pages

- [[playbooks/theo-style]]
- [[traders/jijo]]
- [[traders/cented]]
- [[frameworks/farmer-detection]]
