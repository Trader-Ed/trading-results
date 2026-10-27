# Early-session variants, ATR pick, 2026-06-01 to 2026-10-23, $2,500 equity (run 2026-10-27)

All four use the current exits and 2% slippage per side; they differ only in when entries start and
how the first half hour is handled:

- **9:40 baseline**: entries from 9:40, VWAP checks always on (the rulebook before 2026-10-27).
- **9:35 + VWAP warm-up**: entries from 9:35; before 10:00 every VWAP check is skipped (VWAP step,
  VWAP as a pullback level, chop filter, VWAP in the setup-failed exit). The current rulebook.
- **(a)**: entries from 9:35 with VWAP checks always on (no warm-up).
- **(b)**: entries from 9:35, but before 10:00 only the squeeze rule can enter; the regular rules start
  at 10:00. Otherwise as the current rulebook (warm-up kept, so it only affects the setup-failed exit
  of a squeeze trade opened before 10:00).

| Variant | Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|
| 9:40 baseline (no warm-up) | 84 | 36.9% | $37.24 | $-29.73 | $-421.47 | $-5.02 | +13.8% ($+346.00) | -8.1% ($-201.91) |
| 9:35 + VWAP warm-up to 10:00 | 95 | 36.8% | $37.95 | $-33.62 | $-689.17 | $-7.25 | +17.3% ($+432.77) | -8.1% ($-201.91) |
| (a) 9:35, no VWAP warm-up | 90 | 36.7% | $37.50 | $-31.91 | $-581.38 | $-6.46 | +13.8% ($+346.00) | -8.1% ($-201.91) |
| (b) 9:35, squeeze only before 10:00 | 83 | 38.6% | $36.80 | $-30.80 | $-393.07 | $-4.74 | +13.8% ($+346.00) | -8.1% ($-201.91) |

### Entries before 10:00 and from 10:00

| Variant | Before 10:00: trades | win rate | P&L | From 10:00: trades | win rate | P&L |
|---|---|---|---|---|---|---|
| 9:40 baseline (no warm-up) | 3 | 33.3% | $+4.10 | 81 | 37.0% | $-425.57 |
| 9:35 + VWAP warm-up to 10:00 | 14 | 35.7% | $-263.60 | 81 | 37.0% | $-425.57 |
| (a) 9:35, no VWAP warm-up | 9 | 33.3% | $-155.81 | 81 | 37.0% | $-425.57 |
| (b) 9:35, squeeze only before 10:00 | 3 | 66.7% | $+28.50 | 80 | 37.5% | $-421.57 |

### By setup

| Variant | Pullback: trades | P&L | Squeeze: trades | P&L |
|---|---|---|---|---|
| 9:40 baseline (no warm-up) | 45 | $-459.70 | 39 | $+38.23 |
| 9:35 + VWAP warm-up to 10:00 | 54 | $-708.68 | 41 | $+19.51 |
| (a) 9:35, no VWAP warm-up | 49 | $-600.89 | 41 | $+19.51 |
| (b) 9:35, squeeze only before 10:00 | 42 | $-412.58 | 41 | $+19.51 |

## 9:40 baseline

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

## 9:35 + VWAP warm-up

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

## (a) 9:35, no VWAP warm-up

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 90 | 36.7% | $+37.50 | $-31.91 | $-581.38 | $-6.46 | $+346.00 | $-135.50 | $+346.00 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 28 | 32.1% | $+92.19 | $+3.29 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| TSLA | 41 | 39.0% | $-82.40 | $-2.01 |
| META | 20 | 40.0% | $-554.82 | $-27.74 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 33 | 48.5% | $-12.34 | $-0.37 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 6 | 0.0% | $-378.62 | $-63.10 |
| trailing_stop | 45 | 33.3% | $-546.20 | $-12.14 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 46 | 32.6% | $-10.98 | $-0.24 |
| short | 44 | 40.9% | $-570.40 | $-12.96 |

## (b) 9:35, squeeze only before 10:00

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 38.6% | $+36.80 | $-30.80 | $-393.07 | $-4.74 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 26 | 34.6% | $+123.39 | $+4.75 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| TSLA | 37 | 40.5% | $-60.79 | $-1.64 |
| META | 19 | 42.1% | $-419.32 | $-22.07 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 30 | 53.3% | $+22.14 | $+0.74 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 6 | 0.0% | $-378.62 | $-63.10 |
| trailing_stop | 41 | 34.1% | $-392.37 | $-9.57 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 44 | 34.1% | $+8.94 | $+0.20 |
| short | 39 | 43.6% | $-402.01 | $-10.31 |

---

Full per-trade tables: [history/2026-10-27-early-session.md](history/2026-10-27-early-session.md)
