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

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.68 | 10:13 | 1.32 | hard_stop | $-36.35 |
| 2 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.42 | 10:46 | 2.74 | trailing_stop | $+32.66 |
| 3 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 6.01 | 10:48 | 6.40 | volume_faded | $+39.16 |
| 4 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 10:34 | 3.21 | 10:36 | 2.99 | volume_faded | $-22.40 |
| 5 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 11:47 | 2.92 | 11:48 | 2.28 | hard_stop | $-63.38 |
| 6 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.59 | 10:57 | 2.26 | volume_faded | $-32.70 |
| 7 | 2026-06-22 | TSLA | long | pullback | TSLA260622C00410000 | 11:44 | 2.61 | 11:45 | 2.29 | volume_faded | $-31.80 |
| 8 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.11 | 11:55 | 1.66 | trailing_stop | $-45.61 |
| 9 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.48 | 11:19 | 1.32 | trailing_stop | $-16.19 |
| 10 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 09:53 | 2.90 | volume_faded | $-15.92 |
| 11 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 10:43 | 1.97 | 10:43 | 1.54 | trailing_stop | $-42.52 |
| 12 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 11:08 | 2.28 | 11:11 | 1.97 | trailing_stop | $-31.70 |
| 13 | 2026-06-29 | TSLA | long | pullback | TSLA260629C00392500 | 10:26 | 3.11 | 10:28 | 4.57 | profit_target | $+146.22 |
| 14 | 2026-06-29 | TSLA | long | squeeze | TSLA260629C00400000 | 11:28 | 1.52 | 11:28 | 1.19 | trailing_stop | $-32.83 |
| 15 | 2026-06-30 | QQQ | long | squeeze | QQQ260630C00734000 | 11:35 | 1.49 | 11:38 | 1.17 | trailing_stop | $-32.10 |
| 16 | 2026-07-01 | TSLA | long | squeeze | TSLA260701C00430000 | 10:48 | 1.78 | 10:50 | 1.72 | trailing_stop | $-7.00 |
| 17 | 2026-07-07 | QQQ | long | squeeze | QQQ260707C00708000 | 11:45 | 1.73 | 11:49 | 1.87 | trailing_stop | $+13.19 |
| 18 | 2026-07-08 | TSLA | long | squeeze | TSLA260708C00397500 | 10:22 | 1.98 | 10:26 | 2.23 | trailing_stop | $+24.78 |
| 19 | 2026-07-10 | TSLA | long | squeeze | TSLA260710C00410000 | 11:17 | 1.42 | 11:19 | 1.22 | trailing_stop | $-19.48 |
| 20 | 2026-07-13 | TSLA | short | squeeze | TSLA260713P00392500 | 10:17 | 1.95 | 10:18 | 1.93 | trailing_stop | $-1.96 |
| 21 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.49 | 11:49 | 2.74 | volume_faded | $+25.52 |
| 22 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:18 | 4.17 | volume_faded | $+40.08 |
| 23 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:57 | 1.78 | trailing_stop | $-15.83 |
| 24 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.86 | 11:27 | 1.81 | volume_faded | $-4.34 |
| 25 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.84 | 11:42 | 3.15 | volume_faded | $+31.02 |
| 26 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.62 | 10:11 | 2.63 | volume_faded | $+0.50 |
| 27 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.83 | 10:36 | 2.84 | volume_faded | $+1.66 |
| 28 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:31 | 2.29 | trailing_stop | $+18.81 |
| 29 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:21 | 2.39 | trailing_stop | $-65.88 |
| 30 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:20 | 3.11 | volume_faded | $+0.58 |
| 31 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.41 | 11:16 | 1.89 | hard_stop | $-52.00 |
| 32 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.98 | 10:46 | 1.85 | volume_faded | $-12.66 |
| 33 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 10:58 | 1.54 | trailing_stop | $+0.66 |
| 34 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.91 | 10:22 | 1.94 | volume_faded | $+3.30 |
| 35 | 2026-08-10 | TSLA | long | squeeze | TSLA260810C00332500 | 10:27 | 1.11 | 10:33 | 1.11 | trailing_stop | $-0.44 |
| 36 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.59 | 11:24 | 1.27 | setup_failed | $-31.72 |
| 37 | 2026-08-11 | QQQ | long | pullback | QQQ260811C00721000 | 10:12 | 2.02 | 10:13 | 1.98 | volume_faded | $-4.00 |
| 38 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.92 | 10:37 | 1.66 | trailing_stop | $+74.41 |
| 39 | 2026-08-13 | QQQ | long | pullback | QQQ260813C00732000 | 11:14 | 1.88 | 11:15 | 1.67 | volume_faded | $-21.08 |
| 40 | 2026-08-17 | TSLA | long | pullback | TSLA260817C00337500 | 10:36 | 3.20 | 10:37 | 3.38 | volume_faded | $+17.82 |
| 41 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.87 | 10:12 | 2.11 | volume_faded | $+24.04 |
| 42 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.75 | 10:42 | 2.50 | volume_faded | $-25.50 |
| 43 | 2026-08-19 | META | long | squeeze | META260819C00550000 | 10:47 | 1.96 | 11:01 | 2.05 | trailing_stop | $+9.57 |
| 44 | 2026-08-21 | META | long | pullback | META260821C00550000 | 10:09 | 3.31 | 10:10 | 3.33 | volume_faded | $+1.70 |
| 45 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.68 | 10:58 | 2.04 | trailing_stop | $+35.54 |
| 46 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.85 | 11:29 | 0.66 | trailing_stop | $-18.29 |
| 47 | 2026-08-25 | QQQ | short | pullback | QQQ260825P00710000 | 11:02 | 1.74 | 11:03 | 1.69 | volume_faded | $-5.86 |
| 48 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 2.01 | 10:20 | 1.65 | trailing_stop | $-36.30 |
| 49 | 2026-08-27 | QQQ | long | pullback | QQQ260827C00717000 | 10:08 | 2.12 | 10:08 | 1.66 | hard_stop | $-45.83 |
| 50 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.47 | 10:42 | 1.15 | trailing_stop | $-31.73 |
| 51 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.18 | 10:41 | 0.96 | trailing_stop | $-22.67 |
| 52 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.39 | 10:18 | 2.21 | trailing_stop | $-17.59 |
| 53 | 2026-08-31 | TSLA | long | pullback | TSLA260831C00362500 | 11:44 | 3.26 | 11:48 | 3.97 | volume_faded | $+70.50 |
| 54 | 2026-09-01 | QQQ | long | pullback | QQQ260901C00708000 | 10:16 | 1.74 | 10:17 | 1.57 | volume_faded | $-17.62 |
| 55 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.23 | 12:00 | 4.69 | noon_shutdown | $+346.00 |
| 56 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 57 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 10:52 | 0.78 | trailing_stop | $-16.22 |
| 58 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.95 | 10:58 | 0.87 | trailing_stop | $-7.84 |
| 59 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:28 | 1.13 | volume_faded | $-17.86 |
| 60 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:37 | 1.38 | trailing_stop | $-10.94 |
| 61 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.55 | 11:37 | 1.77 | volume_faded | $+22.34 |
| 62 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.13 | 10:18 | 2.31 | volume_faded | $+18.10 |
| 63 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 10:18 | 1.59 | trailing_stop | $+33.69 |
| 64 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.30 | 11:15 | 1.12 | setup_failed | $-17.82 |
| 65 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.68 | 11:34 | 1.40 | setup_failed | $-28.16 |
| 66 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.80 | 10:15 | 1.97 | volume_faded | $+17.46 |
| 67 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 10:57 | 2.63 | trailing_stop | $-65.80 |
| 68 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:49 | 2.27 | trailing_stop | $-44.98 |
| 69 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 11:37 | 3.53 | trailing_stop | $+6.00 |
| 70 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.23 | 10:44 | 3.65 | setup_failed | $-58.74 |
| 71 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 4.05 | 11:22 | 3.09 | hard_stop | $-96.24 |
| 72 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.70 | trailing_stop | $-46.93 |
| 73 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:53 | 1.63 | trailing_stop | $-14.41 |
| 74 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00742000 | 11:20 | 1.24 | 11:22 | 1.22 | volume_faded | $-2.92 |
| 75 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.66 | 10:08 | 5.24 | volume_faded | $-41.80 |
| 76 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:13 | 2.90 | trailing_stop | $+25.90 |
| 77 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 11:40 | 2.69 | trailing_stop | $+7.40 |
| 78 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 79 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.93 | 11:48 | 3.08 | hard_stop | $-84.82 |
| 80 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 10:44 | 3.21 | trailing_stop | $-5.98 |
| 81 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.25 | 11:47 | 2.00 | volume_faded | $-25.50 |
| 82 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 4.03 | 10:42 | 4.21 | volume_faded | $+18.50 |
| 83 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.52 | 10:51 | 4.04 | volume_faded | $-48.10 |
| 84 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:24 | 2.56 | trailing_stop | $-52.26 |

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

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.68 | 10:13 | 1.32 | hard_stop | $-36.35 |
| 2 | 2026-06-10 | TSLA | long | pullback | TSLA260610C00395000 | 09:39 | 5.20 | 09:40 | 4.08 | hard_stop | $-112.36 |
| 3 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.42 | 10:46 | 2.74 | trailing_stop | $+32.66 |
| 4 | 2026-06-12 | TSLA | long | pullback | TSLA260612C00400000 | 09:36 | 7.03 | 09:37 | 6.87 | trailing_stop | $-15.80 |
| 5 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 6.01 | 10:48 | 6.40 | volume_faded | $+39.16 |
| 6 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 10:34 | 3.21 | 10:36 | 2.99 | volume_faded | $-22.40 |
| 7 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 11:47 | 2.92 | 11:48 | 2.28 | hard_stop | $-63.38 |
| 8 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.59 | 10:57 | 2.26 | volume_faded | $-32.70 |
| 9 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00397500 | 09:35 | 3.21 | 09:36 | 2.79 | trailing_stop | $-42.00 |
| 10 | 2026-06-22 | TSLA | long | squeeze | TSLA260622C00400000 | 09:38 | 3.06 | 09:40 | 3.29 | trailing_stop | $+23.28 |
| 11 | 2026-06-22 | TSLA | long | pullback | TSLA260622C00410000 | 11:44 | 2.61 | 11:45 | 2.29 | volume_faded | $-31.80 |
| 12 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.11 | 11:55 | 1.66 | trailing_stop | $-45.61 |
| 13 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.48 | 11:19 | 1.32 | trailing_stop | $-16.19 |
| 14 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 09:53 | 2.90 | volume_faded | $-15.92 |
| 15 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 10:43 | 1.97 | 10:43 | 1.54 | trailing_stop | $-42.52 |
| 16 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 11:08 | 2.28 | 11:11 | 1.97 | trailing_stop | $-31.70 |
| 17 | 2026-06-29 | TSLA | long | pullback | TSLA260629C00392500 | 10:26 | 3.11 | 10:28 | 4.57 | profit_target | $+146.22 |
| 18 | 2026-06-29 | TSLA | long | squeeze | TSLA260629C00400000 | 11:28 | 1.52 | 11:28 | 1.19 | trailing_stop | $-32.83 |
| 19 | 2026-06-30 | QQQ | long | squeeze | QQQ260630C00734000 | 11:35 | 1.49 | 11:38 | 1.17 | trailing_stop | $-32.10 |
| 20 | 2026-07-01 | TSLA | long | squeeze | TSLA260701C00430000 | 10:48 | 1.78 | 10:50 | 1.72 | trailing_stop | $-7.00 |
| 21 | 2026-07-06 | TSLA | short | pullback | TSLA260706P00392500 | 09:37 | 4.31 | 09:39 | 3.81 | trailing_stop | $-50.91 |
| 22 | 2026-07-07 | QQQ | long | squeeze | QQQ260707C00708000 | 11:45 | 1.73 | 11:49 | 1.87 | trailing_stop | $+13.19 |
| 23 | 2026-07-08 | TSLA | long | squeeze | TSLA260708C00397500 | 10:22 | 1.98 | 10:26 | 2.23 | trailing_stop | $+24.78 |
| 24 | 2026-07-10 | TSLA | long | squeeze | TSLA260710C00410000 | 11:17 | 1.42 | 11:19 | 1.22 | trailing_stop | $-19.48 |
| 25 | 2026-07-13 | TSLA | short | squeeze | TSLA260713P00392500 | 10:17 | 1.95 | 10:18 | 1.93 | trailing_stop | $-1.96 |
| 26 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.49 | 11:49 | 2.74 | volume_faded | $+25.52 |
| 27 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:18 | 4.17 | volume_faded | $+40.08 |
| 28 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:57 | 1.78 | trailing_stop | $-15.83 |
| 29 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.86 | 11:27 | 1.81 | volume_faded | $-4.34 |
| 30 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.84 | 11:42 | 3.15 | volume_faded | $+31.02 |
| 31 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.62 | 10:11 | 2.63 | volume_faded | $+0.50 |
| 32 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.83 | 10:36 | 2.84 | volume_faded | $+1.66 |
| 33 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:31 | 2.29 | trailing_stop | $+18.81 |
| 34 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:21 | 2.39 | trailing_stop | $-65.88 |
| 35 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:20 | 3.11 | volume_faded | $+0.58 |
| 36 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.41 | 11:16 | 1.89 | hard_stop | $-52.00 |
| 37 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.98 | 10:46 | 1.85 | volume_faded | $-12.66 |
| 38 | 2026-08-05 | TSLA | long | pullback | TSLA260805C00325000 | 09:42 | 3.26 | 09:42 | 2.56 | hard_stop | $-70.50 |
| 39 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 10:58 | 1.54 | trailing_stop | $+0.66 |
| 40 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.91 | 10:22 | 1.94 | volume_faded | $+3.30 |
| 41 | 2026-08-10 | TSLA | long | squeeze | TSLA260810C00332500 | 10:27 | 1.11 | 10:33 | 1.11 | trailing_stop | $-0.44 |
| 42 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.59 | 11:24 | 1.27 | setup_failed | $-31.72 |
| 43 | 2026-08-11 | QQQ | long | pullback | QQQ260811C00721000 | 10:12 | 2.02 | 10:13 | 1.98 | volume_faded | $-4.00 |
| 44 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.92 | 10:37 | 1.66 | trailing_stop | $+74.41 |
| 45 | 2026-08-13 | QQQ | long | pullback | QQQ260813C00732000 | 11:14 | 1.88 | 11:15 | 1.67 | volume_faded | $-21.08 |
| 46 | 2026-08-17 | TSLA | long | pullback | TSLA260817C00337500 | 10:36 | 3.20 | 10:37 | 3.38 | volume_faded | $+17.82 |
| 47 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.87 | 10:12 | 2.11 | volume_faded | $+24.04 |
| 48 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.75 | 10:42 | 2.50 | volume_faded | $-25.50 |
| 49 | 2026-08-19 | META | long | squeeze | META260819C00550000 | 10:47 | 1.96 | 11:01 | 2.05 | trailing_stop | $+9.57 |
| 50 | 2026-08-21 | META | long | pullback | META260821C00550000 | 10:09 | 3.31 | 10:10 | 3.33 | volume_faded | $+1.70 |
| 51 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.68 | 10:58 | 2.04 | trailing_stop | $+35.54 |
| 52 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.85 | 11:29 | 0.66 | trailing_stop | $-18.29 |
| 53 | 2026-08-25 | QQQ | short | pullback | QQQ260825P00710000 | 11:02 | 1.74 | 11:03 | 1.69 | volume_faded | $-5.86 |
| 54 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 2.01 | 10:20 | 1.65 | trailing_stop | $-36.30 |
| 55 | 2026-08-27 | QQQ | long | pullback | QQQ260827C00717000 | 10:08 | 2.12 | 10:08 | 1.66 | hard_stop | $-45.83 |
| 56 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.47 | 10:42 | 1.15 | trailing_stop | $-31.73 |
| 57 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.18 | 10:41 | 0.96 | trailing_stop | $-22.67 |
| 58 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.39 | 10:18 | 2.21 | trailing_stop | $-17.59 |
| 59 | 2026-08-31 | TSLA | long | pullback | TSLA260831C00362500 | 11:44 | 3.26 | 11:48 | 3.97 | volume_faded | $+70.50 |
| 60 | 2026-09-01 | QQQ | long | pullback | QQQ260901C00708000 | 10:16 | 1.74 | 10:17 | 1.57 | volume_faded | $-17.62 |
| 61 | 2026-09-02 | TSLA | short | pullback | TSLA260902P00355000 | 09:37 | 3.40 | 09:40 | 3.99 | trailing_stop | $+59.78 |
| 62 | 2026-09-03 | QQQ | long | pullback | QQQ260903C00711000 | 09:38 | 1.85 | 09:39 | 2.71 | profit_target | $+86.77 |
| 63 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.23 | 12:00 | 4.69 | noon_shutdown | $+346.00 |
| 64 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 65 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 10:52 | 0.78 | trailing_stop | $-16.22 |
| 66 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.95 | 10:58 | 0.87 | trailing_stop | $-7.84 |
| 67 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:28 | 1.13 | volume_faded | $-17.86 |
| 68 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:37 | 1.38 | trailing_stop | $-10.94 |
| 69 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.55 | 11:37 | 1.77 | volume_faded | $+22.34 |
| 70 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00362500 | 09:37 | 3.21 | 09:40 | 3.07 | volume_faded | $-14.56 |
| 71 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.13 | 10:18 | 2.31 | volume_faded | $+18.10 |
| 72 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 10:18 | 1.59 | trailing_stop | $+33.69 |
| 73 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.30 | 11:15 | 1.12 | setup_failed | $-17.82 |
| 74 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.68 | 11:34 | 1.40 | setup_failed | $-28.16 |
| 75 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.80 | 10:15 | 1.97 | volume_faded | $+17.46 |
| 76 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 10:57 | 2.63 | trailing_stop | $-65.80 |
| 77 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:49 | 2.27 | trailing_stop | $-44.98 |
| 78 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 11:37 | 3.53 | trailing_stop | $+6.00 |
| 79 | 2026-10-01 | QQQ | short | pullback | QQQ261001P00742000 | 09:44 | 2.70 | 09:45 | 2.74 | volume_faded | $+4.10 |
| 80 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.23 | 10:44 | 3.65 | setup_failed | $-58.74 |
| 81 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 4.05 | 11:22 | 3.09 | hard_stop | $-96.24 |
| 82 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.70 | trailing_stop | $-46.93 |
| 83 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:53 | 1.63 | trailing_stop | $-14.41 |
| 84 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00742000 | 11:20 | 1.24 | 11:22 | 1.22 | volume_faded | $-2.92 |
| 85 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.66 | 10:08 | 5.24 | volume_faded | $-41.80 |
| 86 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:13 | 2.90 | trailing_stop | $+25.90 |
| 87 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 11:40 | 2.69 | trailing_stop | $+7.40 |
| 88 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 89 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.93 | 11:48 | 3.08 | hard_stop | $-84.82 |
| 90 | 2026-10-19 | META | short | pullback | META261019P00702500 | 09:39 | 6.27 | 09:40 | 4.92 | trailing_stop | $-135.50 |
| 91 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 10:44 | 3.21 | trailing_stop | $-5.98 |
| 92 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.25 | 11:47 | 2.00 | volume_faded | $-25.50 |
| 93 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 4.03 | 10:42 | 4.21 | volume_faded | $+18.50 |
| 94 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.52 | 10:51 | 4.04 | volume_faded | $-48.10 |
| 95 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:24 | 2.56 | trailing_stop | $-52.26 |
