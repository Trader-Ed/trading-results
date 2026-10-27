# Backtest: 9:35 entries + VWAP warm-up vs previous baseline

ATR pick, 2026-06-01 to 2026-10-23, $2,500 equity, 2% slippage per side.

- **New:** first entry 09:35; VWAP checks skipped before 10:00 (30-minute warm-up).
- **Previous:** first entry 09:40; no warm-up.

| | Previous (9:40, no warm-up) | New (9:35, warm-up) | Change |
|---|---|---|---|
| Trades | 84 | 95 | +11 |
| Win rate | 36.9% | 36.8% | −0.1 pt |
| P&L after costs | −$421.47 | −$689.17 | −$267.70 |
| P&L per trade | −$5.02 | −$7.25 | −$2.23 |

## Trades entered 9:35–10:00

| | Previous | New |
|---|---|---|
| Trades | 3 | 14 |
| Win rate | 33.3% | 35.7% |
| P&L after costs | +$4.10 | −$263.60 |
| P&L per trade | +$1.37 | −$18.83 |

Of the new run's 14 early trades, 9 were entered 9:35–9:39 (before the old first-entry time): 33.3% win rate, −$201.30.

By setup (new run, 9:35–10:00):

| Setup | Side | Trades | P&L | Per trade |
|---|---|---|---|---|
| pullback | long | 5 | −$127.81 | −$25.56 |
| pullback | short | 6 | −$164.29 | −$27.38 |
| squeeze | long | 1 | +$23.28 | +$23.28 |
| squeeze | short | 2 | +$5.22 | +$2.61 |

## What changed

- All 84 previous trades appear unchanged in the new run (same day, name, minute, side, setup; trades from 10:00 on total −$425.57 in both).
- The new settings only **added** 11 trades, all before 10:00, totalling −$267.70 (−$24.34 per trade).
- The early pullback trades did badly (11 trades, −$292.10); the 3 early squeeze trades were slightly positive.

## Previous (9:40, no warm-up)

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 84 | 36.9% | $+37.24 | $-29.73 | $-421.47 | $-5.02 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 28 | 32.1% | $+92.19 | $+3.29 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| TSLA | 36 | 38.9% | $-57.99 | $-1.61 |
| META | 19 | 42.1% | $-419.32 | $-22.07 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 32 | 50.0% | $+2.22 | $+0.07 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 6 | 0.0% | $-378.62 | $-63.10 |
| trailing_stop | 40 | 32.5% | $-400.85 | $-10.02 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 45 | 31.1% | $-34.26 | $-0.76 |
| short | 39 | 43.6% | $-387.21 | $-9.93 |

## New (9:35, VWAP warm-up)

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 95 | 36.8% | $+37.95 | $-33.62 | $-689.17 | $-7.25 | $+346.00 | $-135.50 | $+432.77 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 30 | 36.7% | $+183.06 | $+6.10 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| TSLA | 44 | 36.4% | $-281.06 | $-6.39 |
| META | 20 | 40.0% | $-554.82 | $-27.74 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 2 | 100.0% | $+232.99 | $+116.50 |
| volume_faded | 34 | 50.0% | $-8.24 | $-0.24 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 8 | 0.0% | $-561.48 | $-70.19 |
| trailing_stop | 46 | 32.6% | $-562.00 | $-12.22 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 50 | 32.0% | $-122.87 | $-2.46 |
| short | 45 | 42.2% | $-566.30 | $-12.58 |

---

Full per-trade tables: [history/2026-10-27-vwap-warmup-935-vs-prev-baseline.md](history/2026-10-27-vwap-warmup-935-vs-prev-baseline.md)
