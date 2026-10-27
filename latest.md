# T6, ATR pick, 2026-06-01 to 2026-10-23, $2,500 equity (run 2026-10-27)

All four start from the new default rulebook (partner decision 2026-10-27): entries from 9:35, squeeze
rule only before 10:00, regular (pullback) rules from 10:00, VWAP warm-up to 10:00, 2% slippage per side.

- **New default**: as above.
- **(a)**: squeeze rule only, all morning (no pullback entries at all).
- **(b)**: as (a), with the squeeze trailing stop at 30% instead of 20%.
- **(c)**: pullback entries only when the day's name is QQQ or TSLA; squeeze on every name.

| Variant | Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|
| New default | 83 | 38.6% | $36.80 | $-30.80 | $-393.07 | $-4.74 | +13.8% ($+346.00) | -8.1% ($-201.91) |
| (a) squeeze only | 42 | 35.7% | $46.61 | $-27.32 | $-38.41 | $-0.91 | +13.8% ($+346.00) | -3.0% ($-74.22) |
| (b) squeeze only, 30% trail | 41 | 34.1% | $98.94 | $-39.25 | $+325.22 | $+7.93 | +13.8% ($+346.00) | -4.7% ($-118.10) |
| (c) pullback only on QQQ, TSLA | 74 | 40.5% | $38.58 | $-26.80 | $-21.72 | $-0.29 | +13.8% ($+346.00) | -3.8% ($-96.13) |

### By setup, all runs

| Variant | Pullback: trades | win rate | P&L | Squeeze: trades | win rate | P&L |
|---|---|---|---|---|---|---|
| New default | 42 | 40.5% | $-412.58 | 41 | 36.6% | $+19.51 |
| (a) squeeze only | 0 | - | $+0.00 | 42 | 35.7% | $-38.41 |
| (b) squeeze only, 30% trail | 0 | - | $+0.00 | 41 | 34.1% | $+325.22 |
| (c) pullback only on QQQ, TSLA | 33 | 45.5% | $-41.23 | 41 | 36.6% | $+19.51 |

### How much rides on one trade

One squeeze trade, QQQ on 2026-09-03 (+$346.00, closed at the noon shutdown), is in all four runs.
Without it every variant loses money:

| Variant | Total P&L | Without that trade | Without the best 3 trades |
|---|---|---|---|
| New default | $-393.07 | $-739.07 | $-959.70 |
| (a) squeeze only | $-38.41 | $-384.41 | $-506.04 |
| (b) squeeze only, 30% trail | $+325.22 | $-20.78 | $-435.03 |
| (c) pullback only on QQQ, TSLA | $-21.72 | $-367.72 | $-588.35 |

## New default

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 38.6% | $+36.80 | $-30.80 | $-393.07 | $-4.74 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 41 | 36.6% | $+19.51 | $+0.48 |
| pullback | 42 | 40.5% | $-412.58 | $-9.82 |

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

## (a) squeeze only

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 42 | 35.7% | $+46.61 | $-27.32 | $-38.41 | $-0.91 | $+346.00 | $-65.80 | $+346.00 | $-74.22 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 42 | 35.7% | $-38.41 | $-0.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 9 | 33.3% | $+231.24 | $+25.69 |
| META | 11 | 54.5% | $-84.32 | $-7.67 |
| TSLA | 22 | 27.3% | $-185.33 | $-8.42 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| trailing_stop | 41 | 34.1% | $-384.41 | $-9.38 |

## (b) squeeze only, 30% trail

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 41 | 34.1% | $+98.94 | $-39.25 | $+325.22 | $+7.93 | $+346.00 | $-95.20 | $+346.00 | $-118.10 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 41 | 34.1% | $+325.22 | $+7.93 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 8 | 62.5% | $+470.55 | $+58.82 |
| META | 11 | 45.5% | $+182.90 | $+16.63 |
| TSLA | 22 | 18.2% | $-328.23 | $-14.92 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 6 | 83.3% | $+734.40 | $+122.40 |
| trailing_stop | 35 | 25.7% | $-409.18 | $-11.69 |

## (c) pullback only on QQQ, TSLA

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 74 | 40.5% | $+38.58 | $-26.80 | $-21.72 | $-0.29 | $+346.00 | $-65.88 | $+346.00 | $-96.13 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 41 | 36.6% | $+19.51 | $+0.48 |
| pullback | 33 | 45.5% | $-41.23 | $-1.25 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 26 | 34.6% | $+123.39 | $+4.75 |
| TSLA | 37 | 40.5% | $-60.79 | $-1.64 |
| META | 11 | 54.5% | $-84.32 | $-7.67 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 25 | 56.0% | $+117.34 | $+4.69 |
| setup_failed | 3 | 0.0% | $-77.70 | $-25.90 |
| hard_stop | 3 | 0.0% | $-161.21 | $-53.74 |
| trailing_stop | 41 | 34.1% | $-392.37 | $-9.57 |

---

Full per-trade tables: [history/2026-10-27-t6.md](history/2026-10-27-t6.md)
