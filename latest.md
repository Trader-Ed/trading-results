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

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 39 | 35.9% | $+38.23 | $+0.98 |
| pullback | 45 | 37.8% | $-459.70 | $-10.22 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 32 | 50.0% | $+2.22 | $+0.07 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 6 | 0.0% | $-378.62 | $-63.10 |
| trailing_stop | 40 | 32.5% | $-400.85 | $-10.02 |

### Entries before 10:00

3 trades, win rate 33.3%, total $+4.10.

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 09:53 | 2.90 | volume_faded | $-15.92 |
| 2 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 3 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |

## 9:35 + VWAP warm-up

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 95 | 36.8% | $+37.95 | $-33.62 | $-689.17 | $-7.25 | $+346.00 | $-135.50 | $+432.77 | $-201.91 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 41 | 36.6% | $+19.51 | $+0.48 |
| pullback | 54 | 37.0% | $-708.68 | $-13.12 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 2 | 100.0% | $+232.99 | $+116.50 |
| volume_faded | 34 | 50.0% | $-8.24 | $-0.24 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 8 | 0.0% | $-561.48 | $-70.19 |
| trailing_stop | 46 | 32.6% | $-562.00 | $-12.22 |

### Entries before 10:00

14 trades, win rate 35.7%, total $-263.60.

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-10 | TSLA | long | pullback | TSLA260610C00395000 | 09:39 | 5.20 | 09:40 | 4.08 | hard_stop | $-112.36 |
| 2 | 2026-06-12 | TSLA | long | pullback | TSLA260612C00400000 | 09:36 | 7.03 | 09:37 | 6.87 | trailing_stop | $-15.80 |
| 3 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00397500 | 09:35 | 3.21 | 09:36 | 2.79 | trailing_stop | $-42.00 |
| 4 | 2026-06-22 | TSLA | long | squeeze | TSLA260622C00400000 | 09:38 | 3.06 | 09:40 | 3.29 | trailing_stop | $+23.28 |
| 5 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 09:53 | 2.90 | volume_faded | $-15.92 |
| 6 | 2026-07-06 | TSLA | short | pullback | TSLA260706P00392500 | 09:37 | 4.31 | 09:39 | 3.81 | trailing_stop | $-50.91 |
| 7 | 2026-08-05 | TSLA | long | pullback | TSLA260805C00325000 | 09:42 | 3.26 | 09:42 | 2.56 | hard_stop | $-70.50 |
| 8 | 2026-09-02 | TSLA | short | pullback | TSLA260902P00355000 | 09:37 | 3.40 | 09:40 | 3.99 | trailing_stop | $+59.78 |
| 9 | 2026-09-03 | QQQ | long | pullback | QQQ260903C00711000 | 09:38 | 1.85 | 09:39 | 2.71 | profit_target | $+86.77 |
| 10 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 11 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00362500 | 09:37 | 3.21 | 09:40 | 3.07 | volume_faded | $-14.56 |
| 12 | 2026-10-01 | QQQ | short | pullback | QQQ261001P00742000 | 09:44 | 2.70 | 09:45 | 2.74 | volume_faded | $+4.10 |
| 13 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 14 | 2026-10-19 | META | short | pullback | META261019P00702500 | 09:39 | 6.27 | 09:40 | 4.92 | trailing_stop | $-135.50 |

## (a) 9:35, no VWAP warm-up

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 90 | 36.7% | $+37.50 | $-31.91 | $-581.38 | $-6.46 | $+346.00 | $-135.50 | $+346.00 | $-201.91 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 41 | 36.6% | $+19.51 | $+0.48 |
| pullback | 49 | 36.7% | $-600.89 | $-12.26 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 33 | 48.5% | $-12.34 | $-0.37 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 6 | 0.0% | $-378.62 | $-63.10 |
| trailing_stop | 45 | 33.3% | $-546.20 | $-12.14 |

### Entries before 10:00

9 trades, win rate 33.3%, total $-155.81.

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00397500 | 09:35 | 3.21 | 09:36 | 2.79 | trailing_stop | $-42.00 |
| 2 | 2026-06-22 | TSLA | long | squeeze | TSLA260622C00400000 | 09:38 | 3.06 | 09:40 | 3.29 | trailing_stop | $+23.28 |
| 3 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 09:53 | 2.90 | volume_faded | $-15.92 |
| 4 | 2026-07-06 | TSLA | short | pullback | TSLA260706P00392500 | 09:37 | 4.31 | 09:39 | 3.81 | trailing_stop | $-50.91 |
| 5 | 2026-09-02 | TSLA | short | pullback | TSLA260902P00355000 | 09:37 | 3.40 | 09:40 | 3.99 | trailing_stop | $+59.78 |
| 6 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 7 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00362500 | 09:37 | 3.21 | 09:40 | 3.07 | volume_faded | $-14.56 |
| 8 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 9 | 2026-10-19 | META | short | pullback | META261019P00702500 | 09:39 | 6.27 | 09:40 | 4.92 | trailing_stop | $-135.50 |

## (b) 9:35, squeeze only before 10:00

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 38.6% | $+36.80 | $-30.80 | $-393.07 | $-4.74 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 41 | 36.6% | $+19.51 | $+0.48 |
| pullback | 42 | 40.5% | $-412.58 | $-9.82 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 30 | 53.3% | $+22.14 | $+0.74 |
| setup_failed | 4 | 0.0% | $-136.44 | $-34.11 |
| hard_stop | 6 | 0.0% | $-378.62 | $-63.10 |
| trailing_stop | 41 | 34.1% | $-392.37 | $-9.57 |

### Entries before 10:00

3 trades, win rate 66.7%, total $+28.50.

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00397500 | 09:35 | 3.21 | 09:36 | 2.79 | trailing_stop | $-42.00 |
| 2 | 2026-06-22 | TSLA | long | squeeze | TSLA260622C00400000 | 09:38 | 3.06 | 09:40 | 3.29 | trailing_stop | $+23.28 |
| 3 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |

---

Full per-trade tables: [history/2026-10-27-early-session.md](history/2026-10-27-early-session.md)
