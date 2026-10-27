# Exit-variant comparison, 2026-06-01 to 2026-10-23, $2,500 equity (run 2026-10-26)

### atr

| Variant | Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|
| baseline | 84 | 36.9% | $37.24 | $-29.73 | $-421.47 | $-5.02 | +13.8% ($+345) | -8.1% ($-202) |
| v0_no_slippage | 84 | 44.0% | $40.13 | $-25.04 | $+308.00 | $+3.67 | +14.3% ($+358) | -6.6% ($-165) |
| v1_volume_fade_3 | 83 | 32.5% | $53.71 | $-31.88 | $-335.39 | $-4.04 | +13.8% ($+345) | -8.1% ($-202) |
| v2_no_volume_fade | 83 | 31.3% | $61.18 | $-33.86 | $-339.36 | $-4.09 | +13.8% ($+345) | -8.1% ($-202) |
| v3_wider_stops | 83 | 37.3% | $60.12 | $-34.38 | $+75.70 | $+0.91 | +13.8% ($+345) | -7.4% ($-185) |
| v4_no_bar_exits | 82 | 31.7% | $64.28 | $-35.37 | $-309.53 | $-3.77 | +13.8% ($+345) | -9.4% ($-235) |

### spy

| Variant | Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|
| baseline | 64 | 25.0% | $31.85 | $-17.62 | $-336.09 | $-5.25 | +4.1% ($+102) | -3.1% ($-78) |
| v0_no_slippage | 64 | 32.8% | $28.70 | $-14.27 | $-10.80 | $-0.17 | +4.3% ($+108) | -2.4% ($-60) |
| v1_volume_fade_3 | 62 | 30.6% | $31.78 | $-21.37 | $-314.92 | $-5.08 | +4.1% ($+102) | -2.6% ($-65) |
| v2_no_volume_fade | 62 | 30.6% | $32.33 | $-22.30 | $-344.64 | $-5.56 | +4.1% ($+102) | -3.1% ($-78) |
| v3_wider_stops | 64 | 23.4% | $42.67 | $-21.87 | $-431.59 | $-6.74 | +5.5% ($+138) | -3.3% ($-82) |
| v4_no_bar_exits | 62 | 35.5% | $32.13 | $-24.86 | $-287.54 | $-4.64 | +4.1% ($+102) | -3.1% ($-78) |

## atr/baseline

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

## atr/v0_no_slippage

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 84 | 44.0% | $+40.13 | $-25.04 | $+308.00 | $+3.67 | $+358.00 | $-82.00 | $+358.00 | $-166.10 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 28 | 42.9% | $+287.00 | $+10.25 |
| TSLA | 36 | 44.4% | $+239.50 | $+6.65 |
| NVDA | 1 | 0.0% | $-33.00 | $-33.00 |
| META | 19 | 47.4% | $-185.50 | $-9.76 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+358.00 | $+358.00 |
| volume_faded | 32 | 59.4% | $+304.00 | $+9.50 |
| profit_target | 1 | 100.0% | $+152.50 | $+152.50 |
| setup_failed | 3 | 0.0% | $-61.00 | $-20.33 |
| trailing_stop | 43 | 37.2% | $-206.30 | $-4.80 |
| hard_stop | 4 | 0.0% | $-239.20 | $-59.80 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 45 | 37.8% | $+334.20 | $+7.43 |
| short | 39 | 51.3% | $-26.20 | $-0.67 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.65 | 10:13 | 1.32 | hard_stop | $-33.00 |
| 2 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.37 | 10:46 | 2.80 | trailing_stop | $+43.00 |
| 3 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 5.89 | 10:48 | 6.53 | volume_faded | $+64.00 |
| 4 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 10:34 | 3.15 | 10:36 | 3.05 | volume_faded | $-10.00 |
| 5 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 11:47 | 2.86 | 11:48 | 2.29 | trailing_stop | $-57.20 |
| 6 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.54 | 10:57 | 2.31 | volume_faded | $-23.00 |
| 7 | 2026-06-22 | TSLA | long | pullback | TSLA260622C00410000 | 11:44 | 2.56 | 11:45 | 2.34 | volume_faded | $-22.00 |
| 8 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.07 | 11:55 | 1.68 | trailing_stop | $-39.00 |
| 9 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.45 | 11:19 | 1.34 | trailing_stop | $-10.60 |
| 10 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.00 | 09:53 | 2.96 | volume_faded | $-4.00 |
| 11 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 10:43 | 1.93 | 10:43 | 1.54 | trailing_stop | $-38.60 |
| 12 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 11:08 | 2.24 | 11:11 | 2.01 | trailing_stop | $-23.20 |
| 13 | 2026-06-29 | TSLA | long | pullback | TSLA260629C00392500 | 10:26 | 3.05 | 10:28 | 4.58 | profit_target | $+152.50 |
| 14 | 2026-06-29 | TSLA | long | squeeze | TSLA260629C00400000 | 11:28 | 1.49 | 11:28 | 1.19 | trailing_stop | $-29.80 |
| 15 | 2026-06-30 | QQQ | long | squeeze | QQQ260630C00734000 | 11:35 | 1.46 | 11:38 | 1.19 | trailing_stop | $-26.80 |
| 16 | 2026-07-01 | TSLA | long | squeeze | TSLA260701C00430000 | 10:48 | 1.75 | 10:50 | 1.75 | trailing_stop | $+0.00 |
| 17 | 2026-07-07 | QQQ | long | squeeze | QQQ260707C00708000 | 11:45 | 1.70 | 11:49 | 1.90 | trailing_stop | $+20.40 |
| 18 | 2026-07-08 | TSLA | long | squeeze | TSLA260708C00397500 | 10:22 | 1.94 | 10:26 | 2.27 | trailing_stop | $+33.20 |
| 19 | 2026-07-10 | TSLA | long | squeeze | TSLA260710C00410000 | 11:17 | 1.39 | 11:19 | 1.25 | trailing_stop | $-14.20 |
| 20 | 2026-07-13 | TSLA | short | squeeze | TSLA260713P00392500 | 10:17 | 1.91 | 10:18 | 1.97 | trailing_stop | $+5.80 |
| 21 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.44 | 11:49 | 2.80 | volume_faded | $+36.00 |
| 22 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.70 | 10:18 | 4.26 | volume_faded | $+56.00 |
| 23 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.90 | 10:57 | 1.82 | trailing_stop | $-8.40 |
| 24 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.82 | 11:27 | 1.85 | volume_faded | $+3.00 |
| 25 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.78 | 11:42 | 3.21 | volume_faded | $+43.00 |
| 26 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.57 | 10:11 | 2.68 | volume_faded | $+11.00 |
| 27 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.77 | 10:36 | 2.90 | volume_faded | $+13.00 |
| 28 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.06 | 10:31 | 2.34 | trailing_stop | $+27.60 |
| 29 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 2.99 | 11:21 | 2.39 | trailing_stop | $-59.80 |
| 30 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.04 | 10:20 | 3.17 | volume_faded | $+13.00 |
| 31 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.36 | 11:16 | 1.89 | hard_stop | $-47.20 |
| 32 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.94 | 10:46 | 1.89 | volume_faded | $-5.00 |
| 33 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.50 | 10:58 | 1.57 | trailing_stop | $+6.80 |
| 34 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.87 | 10:22 | 1.98 | volume_faded | $+11.00 |
| 35 | 2026-08-10 | TSLA | long | squeeze | TSLA260810C00332500 | 10:27 | 1.09 | 10:33 | 1.13 | trailing_stop | $+4.00 |
| 36 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.56 | 11:24 | 1.30 | setup_failed | $-26.00 |
| 37 | 2026-08-11 | QQQ | long | pullback | QQQ260811C00721000 | 10:12 | 1.98 | 10:13 | 2.02 | volume_faded | $+4.00 |
| 38 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.90 | 10:37 | 1.70 | trailing_stop | $+79.60 |
| 39 | 2026-08-13 | QQQ | long | pullback | QQQ260813C00732000 | 11:14 | 1.84 | 11:15 | 1.70 | volume_faded | $-14.00 |
| 40 | 2026-08-17 | TSLA | long | pullback | TSLA260817C00337500 | 10:36 | 3.14 | 10:37 | 3.45 | volume_faded | $+31.00 |
| 41 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.83 | 10:12 | 2.15 | volume_faded | $+32.00 |
| 42 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.70 | 10:42 | 2.55 | volume_faded | $-15.00 |
| 43 | 2026-08-19 | META | long | squeeze | META260819C00550000 | 10:47 | 1.92 | 11:01 | 2.10 | trailing_stop | $+17.60 |
| 44 | 2026-08-21 | META | long | pullback | META260821C00550000 | 10:09 | 3.25 | 10:10 | 3.40 | volume_faded | $+15.00 |
| 45 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.65 | 10:58 | 2.08 | trailing_stop | $+43.00 |
| 46 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.83 | 11:29 | 0.67 | trailing_stop | $-15.80 |
| 47 | 2026-08-25 | QQQ | short | pullback | QQQ260825P00710000 | 11:02 | 1.71 | 11:03 | 1.72 | volume_faded | $+1.00 |
| 48 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 1.97 | 10:20 | 1.68 | trailing_stop | $-29.00 |
| 49 | 2026-08-27 | QQQ | long | pullback | QQQ260827C00717000 | 10:08 | 2.08 | 10:09 | 1.86 | volume_faded | $-22.00 |
| 50 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.44 | 10:48 | 1.20 | trailing_stop | $-24.00 |
| 51 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.16 | 10:41 | 0.98 | trailing_stop | $-18.40 |
| 52 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.34 | 10:18 | 2.26 | trailing_stop | $-8.40 |
| 53 | 2026-08-31 | TSLA | long | pullback | TSLA260831C00362500 | 11:44 | 3.20 | 11:48 | 4.05 | volume_faded | $+85.00 |
| 54 | 2026-09-01 | QQQ | long | pullback | QQQ260901C00708000 | 10:16 | 1.71 | 10:17 | 1.60 | volume_faded | $-11.00 |
| 55 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.21 | 12:00 | 4.79 | noon_shutdown | $+358.00 |
| 56 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.26 | 09:45 | 2.03 | trailing_stop | $-22.60 |
| 57 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.92 | 10:52 | 0.79 | trailing_stop | $-12.80 |
| 58 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.93 | 10:58 | 0.89 | trailing_stop | $-4.20 |
| 59 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.28 | 11:28 | 1.15 | volume_faded | $-13.00 |
| 60 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.46 | 10:37 | 1.41 | trailing_stop | $-5.20 |
| 61 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.52 | 11:37 | 1.81 | volume_faded | $+29.00 |
| 62 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.09 | 10:18 | 2.36 | volume_faded | $+27.00 |
| 63 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.23 | 10:18 | 1.62 | trailing_stop | $+39.40 |
| 64 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.27 | 11:15 | 1.14 | setup_failed | $-13.00 |
| 65 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.65 | 11:34 | 1.43 | setup_failed | $-22.00 |
| 66 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.76 | 10:14 | 1.76 | trailing_stop | $+0.00 |
| 67 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.22 | 10:57 | 2.68 | trailing_stop | $-54.00 |
| 68 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.67 | 11:49 | 2.32 | trailing_stop | $-35.00 |
| 69 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.40 | 11:37 | 3.60 | trailing_stop | $+20.00 |
| 70 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.15 | 10:44 | 3.73 | trailing_stop | $-41.50 |
| 71 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 3.97 | 11:22 | 3.15 | hard_stop | $-82.00 |
| 72 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.13 | 11:26 | 1.70 | trailing_stop | $-42.60 |
| 73 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.74 | 10:53 | 1.66 | trailing_stop | $-7.60 |
| 74 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00742000 | 11:20 | 1.22 | 11:22 | 1.24 | volume_faded | $+2.00 |
| 75 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.55 | 10:08 | 5.35 | volume_faded | $-20.00 |
| 76 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.59 | 11:13 | 2.96 | trailing_stop | $+37.00 |
| 77 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.56 | 11:40 | 2.74 | trailing_stop | $+18.00 |
| 78 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.14 | 10:00 | 3.75 | trailing_stop | $+61.00 |
| 79 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.85 | 11:48 | 3.08 | hard_stop | $-77.00 |
| 80 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.21 | 10:44 | 3.28 | trailing_stop | $+7.00 |
| 81 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.21 | 11:47 | 2.04 | volume_faded | $-17.00 |
| 82 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 3.95 | 10:42 | 4.30 | volume_faded | $+35.00 |
| 83 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.43 | 10:51 | 4.12 | volume_faded | $-31.00 |
| 84 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.02 | 11:24 | 2.61 | trailing_stop | $-41.00 |

## atr/v1_volume_fade_3

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 32.5% | $+53.71 | $-31.88 | $-335.39 | $-4.04 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 35 | 40.0% | $+155.39 | $+4.44 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| QQQ | 28 | 17.9% | $-103.33 | $-3.69 |
| META | 19 | 42.1% | $-351.10 | $-18.48 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 4 | 100.0% | $+535.50 | $+133.88 |
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| time_stop | 1 | 100.0% | $+69.24 | $+69.24 |
| volume_faded | 9 | 44.4% | $-29.50 | $-3.28 |
| setup_failed | 7 | 0.0% | $-229.98 | $-32.85 |
| hard_stop | 7 | 0.0% | $-435.02 | $-62.15 |
| trailing_stop | 54 | 31.5% | $-591.63 | $-10.96 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 44 | 27.3% | $-106.79 | $-2.43 |
| short | 39 | 38.5% | $-228.60 | $-5.86 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.68 | 10:13 | 1.32 | hard_stop | $-36.35 |
| 2 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.42 | 10:46 | 2.74 | trailing_stop | $+32.66 |
| 3 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 6.01 | 10:50 | 5.73 | volume_faded | $-27.48 |
| 4 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 10:34 | 3.21 | 10:44 | 3.15 | trailing_stop | $-6.43 |
| 5 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 11:47 | 2.92 | 11:48 | 2.28 | hard_stop | $-63.38 |
| 6 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.59 | 10:59 | 2.46 | trailing_stop | $-13.10 |
| 7 | 2026-06-22 | TSLA | long | pullback | TSLA260622C00410000 | 11:44 | 2.61 | 11:46 | 2.05 | hard_stop | $-56.40 |
| 8 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.11 | 11:55 | 1.66 | trailing_stop | $-45.61 |
| 9 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.48 | 11:19 | 1.32 | trailing_stop | $-16.19 |
| 10 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 09:55 | 3.14 | volume_faded | $+7.60 |
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
| 21 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.49 | 11:54 | 2.67 | trailing_stop | $+17.68 |
| 22 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:23 | 5.55 | profit_target | $+177.38 |
| 23 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:57 | 1.78 | trailing_stop | $-15.83 |
| 24 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.86 | 11:28 | 1.64 | trailing_stop | $-21.91 |
| 25 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.84 | 11:46 | 3.53 | time_stop | $+69.24 |
| 26 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.62 | 10:13 | 2.31 | trailing_stop | $-30.93 |
| 27 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.83 | 10:37 | 2.49 | trailing_stop | $-33.34 |
| 28 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:31 | 2.29 | trailing_stop | $+18.81 |
| 29 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:21 | 2.39 | trailing_stop | $-65.88 |
| 30 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:21 | 2.73 | trailing_stop | $-36.59 |
| 31 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.41 | 11:16 | 1.89 | hard_stop | $-52.00 |
| 32 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.98 | 10:50 | 1.71 | setup_failed | $-27.36 |
| 33 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 10:58 | 1.54 | trailing_stop | $+0.66 |
| 34 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.91 | 10:33 | 2.24 | trailing_stop | $+33.57 |
| 35 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.59 | 11:24 | 1.27 | setup_failed | $-31.72 |
| 36 | 2026-08-11 | QQQ | long | pullback | QQQ260811C00721000 | 10:12 | 2.02 | 10:39 | 1.41 | trailing_stop | $-60.84 |
| 37 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.92 | 10:37 | 1.66 | trailing_stop | $+74.41 |
| 38 | 2026-08-13 | QQQ | long | pullback | QQQ260813C00732000 | 11:14 | 1.88 | 11:16 | 1.60 | setup_failed | $-27.94 |
| 39 | 2026-08-17 | TSLA | long | pullback | TSLA260817C00337500 | 10:36 | 3.20 | 10:39 | 3.23 | volume_faded | $+3.12 |
| 40 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.87 | 10:14 | 1.91 | volume_faded | $+4.44 |
| 41 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.75 | 10:43 | 2.37 | setup_failed | $-38.24 |
| 42 | 2026-08-19 | META | long | squeeze | META260819C00550000 | 10:47 | 1.96 | 11:01 | 2.05 | trailing_stop | $+9.57 |
| 43 | 2026-08-21 | META | long | pullback | META260821C00550000 | 10:09 | 3.31 | 10:12 | 3.04 | volume_faded | $-27.70 |
| 44 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.68 | 10:58 | 2.04 | trailing_stop | $+35.54 |
| 45 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.85 | 11:29 | 0.66 | trailing_stop | $-18.29 |
| 46 | 2026-08-25 | QQQ | short | pullback | QQQ260825P00710000 | 11:02 | 1.74 | 11:07 | 1.60 | volume_faded | $-14.68 |
| 47 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 2.01 | 10:20 | 1.65 | trailing_stop | $-36.30 |
| 48 | 2026-08-27 | QQQ | long | pullback | QQQ260827C00717000 | 10:08 | 2.12 | 10:08 | 1.66 | hard_stop | $-45.83 |
| 49 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.47 | 10:42 | 1.15 | trailing_stop | $-31.73 |
| 50 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.18 | 10:41 | 0.96 | trailing_stop | $-22.67 |
| 51 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.39 | 10:18 | 2.21 | trailing_stop | $-17.59 |
| 52 | 2026-08-31 | TSLA | long | pullback | TSLA260831C00362500 | 11:44 | 3.26 | 11:51 | 4.80 | profit_target | $+153.41 |
| 53 | 2026-09-01 | QQQ | long | pullback | QQQ260901C00708000 | 10:16 | 1.74 | 10:18 | 1.54 | trailing_stop | $-20.58 |
| 54 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.23 | 12:00 | 4.69 | noon_shutdown | $+346.00 |
| 55 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 56 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 10:52 | 0.78 | trailing_stop | $-16.22 |
| 57 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.95 | 10:58 | 0.87 | trailing_stop | $-7.84 |
| 58 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:32 | 1.02 | trailing_stop | $-28.20 |
| 59 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:37 | 1.38 | trailing_stop | $-10.94 |
| 60 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.55 | 11:38 | 1.52 | trailing_stop | $-3.10 |
| 61 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.13 | 10:20 | 2.30 | trailing_stop | $+16.63 |
| 62 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 10:18 | 1.59 | trailing_stop | $+33.69 |
| 63 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.30 | 11:15 | 1.12 | setup_failed | $-17.82 |
| 64 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.68 | 11:34 | 1.40 | setup_failed | $-28.16 |
| 65 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.80 | 10:17 | 1.78 | volume_faded | $-1.16 |
| 66 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 10:57 | 2.63 | trailing_stop | $-65.80 |
| 67 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:49 | 2.27 | trailing_stop | $-44.98 |
| 68 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 11:37 | 3.53 | trailing_stop | $+6.00 |
| 69 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.23 | 10:44 | 3.65 | setup_failed | $-58.74 |
| 70 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 4.05 | 11:22 | 3.09 | hard_stop | $-96.24 |
| 71 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.70 | trailing_stop | $-46.93 |
| 72 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:53 | 1.63 | trailing_stop | $-14.41 |
| 73 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00742000 | 11:20 | 1.24 | 11:28 | 1.83 | profit_target | $+58.49 |
| 74 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.66 | 10:10 | 6.10 | trailing_stop | $+43.46 |
| 75 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:13 | 2.90 | trailing_stop | $+25.90 |
| 76 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 11:40 | 2.69 | trailing_stop | $+7.40 |
| 77 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 78 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.93 | 11:48 | 3.08 | hard_stop | $-84.82 |
| 79 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 10:44 | 3.21 | trailing_stop | $-5.98 |
| 80 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.25 | 11:49 | 2.09 | volume_faded | $-16.68 |
| 81 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 4.03 | 10:45 | 3.55 | trailing_stop | $-47.54 |
| 82 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.52 | 10:53 | 4.95 | volume_faded | $+43.04 |
| 83 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:24 | 2.56 | trailing_stop | $-52.26 |

## atr/v2_no_volume_fade

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 31.3% | $+61.18 | $-33.86 | $-339.36 | $-4.09 | $+346.00 | $-96.24 | $+346.00 | $-201.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 35 | 40.0% | $+276.62 | $+7.90 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| QQQ | 28 | 14.3% | $-197.51 | $-7.05 |
| META | 19 | 42.1% | $-382.12 | $-20.11 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 5 | 100.0% | $+679.32 | $+135.86 |
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| time_stop | 3 | 100.0% | $+124.22 | $+41.41 |
| setup_failed | 8 | 0.0% | $-260.34 | $-32.54 |
| hard_stop | 7 | 0.0% | $-435.02 | $-62.15 |
| trailing_stop | 59 | 28.8% | $-793.54 | $-13.45 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 44 | 27.3% | $+6.81 | $+0.15 |
| short | 39 | 35.9% | $-346.17 | $-8.88 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.68 | 10:13 | 1.32 | hard_stop | $-36.35 |
| 2 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.42 | 10:46 | 2.74 | trailing_stop | $+32.66 |
| 3 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 6.01 | 10:52 | 5.30 | trailing_stop | $-70.89 |
| 4 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 10:34 | 3.21 | 10:44 | 3.15 | trailing_stop | $-6.43 |
| 5 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 11:47 | 2.92 | 11:48 | 2.28 | hard_stop | $-63.38 |
| 6 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.59 | 10:59 | 2.46 | trailing_stop | $-13.10 |
| 7 | 2026-06-22 | TSLA | long | pullback | TSLA260622C00410000 | 11:44 | 2.61 | 11:46 | 2.05 | hard_stop | $-56.40 |
| 8 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.11 | 11:55 | 1.66 | trailing_stop | $-45.61 |
| 9 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.48 | 11:19 | 1.32 | trailing_stop | $-16.19 |
| 10 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 10:00 | 4.50 | profit_target | $+143.82 |
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
| 21 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.49 | 11:54 | 2.67 | trailing_stop | $+17.68 |
| 22 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:23 | 5.55 | profit_target | $+177.38 |
| 23 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:57 | 1.78 | trailing_stop | $-15.83 |
| 24 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.86 | 11:28 | 1.64 | trailing_stop | $-21.91 |
| 25 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.84 | 11:46 | 3.53 | time_stop | $+69.24 |
| 26 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.62 | 10:13 | 2.31 | trailing_stop | $-30.93 |
| 27 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.83 | 10:37 | 2.49 | trailing_stop | $-33.34 |
| 28 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:31 | 2.29 | trailing_stop | $+18.81 |
| 29 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:21 | 2.39 | trailing_stop | $-65.88 |
| 30 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:21 | 2.73 | trailing_stop | $-36.59 |
| 31 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.41 | 11:16 | 1.89 | hard_stop | $-52.00 |
| 32 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.98 | 10:50 | 1.71 | setup_failed | $-27.36 |
| 33 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 10:58 | 1.54 | trailing_stop | $+0.66 |
| 34 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.91 | 10:33 | 2.24 | trailing_stop | $+33.57 |
| 35 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.59 | 11:24 | 1.27 | setup_failed | $-31.72 |
| 36 | 2026-08-11 | QQQ | long | pullback | QQQ260811C00721000 | 10:12 | 2.02 | 10:39 | 1.41 | trailing_stop | $-60.84 |
| 37 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.92 | 10:37 | 1.66 | trailing_stop | $+74.41 |
| 38 | 2026-08-13 | QQQ | long | pullback | QQQ260813C00732000 | 11:14 | 1.88 | 11:16 | 1.60 | setup_failed | $-27.94 |
| 39 | 2026-08-17 | TSLA | long | pullback | TSLA260817C00337500 | 10:36 | 3.20 | 10:46 | 3.52 | time_stop | $+31.54 |
| 40 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.87 | 10:15 | 1.65 | trailing_stop | $-22.03 |
| 41 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.75 | 10:43 | 2.37 | setup_failed | $-38.24 |
| 42 | 2026-08-19 | META | long | squeeze | META260819C00550000 | 10:47 | 1.96 | 11:01 | 2.05 | trailing_stop | $+9.57 |
| 43 | 2026-08-21 | META | long | pullback | META260821C00550000 | 10:09 | 3.31 | 10:13 | 2.92 | trailing_stop | $-39.12 |
| 44 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.68 | 10:58 | 2.04 | trailing_stop | $+35.54 |
| 45 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.85 | 11:29 | 0.66 | trailing_stop | $-18.29 |
| 46 | 2026-08-25 | QQQ | short | pullback | QQQ260825P00710000 | 11:02 | 1.74 | 11:10 | 1.44 | setup_failed | $-30.36 |
| 47 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 2.01 | 10:20 | 1.65 | trailing_stop | $-36.30 |
| 48 | 2026-08-27 | QQQ | long | pullback | QQQ260827C00717000 | 10:08 | 2.12 | 10:08 | 1.66 | hard_stop | $-45.83 |
| 49 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.47 | 10:42 | 1.15 | trailing_stop | $-31.73 |
| 50 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.18 | 10:41 | 0.96 | trailing_stop | $-22.67 |
| 51 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.39 | 10:18 | 2.21 | trailing_stop | $-17.59 |
| 52 | 2026-08-31 | TSLA | long | pullback | TSLA260831C00362500 | 11:44 | 3.26 | 11:51 | 4.80 | profit_target | $+153.41 |
| 53 | 2026-09-01 | QQQ | long | pullback | QQQ260901C00708000 | 10:16 | 1.74 | 10:18 | 1.54 | trailing_stop | $-20.58 |
| 54 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.23 | 12:00 | 4.69 | noon_shutdown | $+346.00 |
| 55 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 56 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 10:52 | 0.78 | trailing_stop | $-16.22 |
| 57 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.95 | 10:58 | 0.87 | trailing_stop | $-7.84 |
| 58 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:32 | 1.02 | trailing_stop | $-28.20 |
| 59 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:37 | 1.38 | trailing_stop | $-10.94 |
| 60 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.55 | 11:38 | 1.52 | trailing_stop | $-3.10 |
| 61 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.13 | 10:20 | 2.30 | trailing_stop | $+16.63 |
| 62 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 10:18 | 1.59 | trailing_stop | $+33.69 |
| 63 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.30 | 11:15 | 1.12 | setup_failed | $-17.82 |
| 64 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.68 | 11:34 | 1.40 | setup_failed | $-28.16 |
| 65 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.80 | 10:18 | 1.58 | trailing_stop | $-21.18 |
| 66 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 10:57 | 2.63 | trailing_stop | $-65.80 |
| 67 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:49 | 2.27 | trailing_stop | $-44.98 |
| 68 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 11:37 | 3.53 | trailing_stop | $+6.00 |
| 69 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.23 | 10:44 | 3.65 | setup_failed | $-58.74 |
| 70 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 4.05 | 11:22 | 3.09 | hard_stop | $-96.24 |
| 71 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.70 | trailing_stop | $-46.93 |
| 72 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:53 | 1.63 | trailing_stop | $-14.41 |
| 73 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00742000 | 11:20 | 1.24 | 11:28 | 1.83 | profit_target | $+58.49 |
| 74 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.66 | 10:10 | 6.10 | trailing_stop | $+43.46 |
| 75 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:13 | 2.90 | trailing_stop | $+25.90 |
| 76 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 11:40 | 2.69 | trailing_stop | $+7.40 |
| 77 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 78 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.93 | 11:48 | 3.08 | hard_stop | $-84.82 |
| 79 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 10:44 | 3.21 | trailing_stop | $-5.98 |
| 80 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.25 | 11:50 | 1.77 | trailing_stop | $-48.69 |
| 81 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 4.03 | 10:45 | 3.55 | trailing_stop | $-47.54 |
| 82 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.52 | 10:59 | 4.75 | time_stop | $+23.44 |
| 83 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:24 | 2.56 | trailing_stop | $-52.26 |

## atr/v3_wider_stops

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 83 | 37.3% | $+60.12 | $-34.38 | $+75.70 | $+0.91 | $+346.00 | $-95.20 | $+346.00 | $-184.00 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 27 | 40.7% | $+352.30 | $+13.05 |
| NVDA | 1 | 0.0% | $-39.92 | $-39.92 |
| META | 19 | 36.8% | $-79.74 | $-4.20 |
| TSLA | 36 | 36.1% | $-156.94 | $-4.36 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 6 | 83.3% | $+734.40 | $+122.40 |
| profit_target | 1 | 100.0% | $+146.22 | $+146.22 |
| volume_faded | 35 | 45.7% | $-142.72 | $-4.08 |
| setup_failed | 7 | 0.0% | $-303.16 | $-43.31 |
| trailing_stop | 34 | 26.5% | $-359.04 | $-10.56 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 44 | 38.6% | $+328.38 | $+7.46 |
| short | 39 | 35.9% | $-252.68 | $-6.48 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.68 | 10:14 | 1.28 | setup_failed | $-39.92 |
| 2 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.42 | 10:47 | 2.40 | trailing_stop | $-1.64 |
| 3 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 6.01 | 10:48 | 6.40 | volume_faded | $+39.16 |
| 4 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 10:34 | 3.21 | 10:36 | 2.99 | volume_faded | $-22.40 |
| 5 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 11:47 | 2.92 | 11:49 | 2.17 | setup_failed | $-75.14 |
| 6 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.59 | 10:57 | 2.26 | volume_faded | $-32.70 |
| 7 | 2026-06-22 | TSLA | long | pullback | TSLA260622C00410000 | 11:44 | 2.61 | 11:45 | 2.29 | volume_faded | $-31.80 |
| 8 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.11 | 12:00 | 1.96 | noon_shutdown | $-15.14 |
| 9 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.48 | 11:21 | 1.15 | trailing_stop | $-32.65 |
| 10 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 09:53 | 2.90 | volume_faded | $-15.92 |
| 11 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 10:43 | 1.97 | 10:43 | 1.35 | trailing_stop | $-61.81 |
| 12 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 11:08 | 2.28 | 11:12 | 1.72 | trailing_stop | $-56.29 |
| 13 | 2026-06-29 | TSLA | long | pullback | TSLA260629C00392500 | 10:26 | 3.11 | 10:28 | 4.57 | profit_target | $+146.22 |
| 14 | 2026-06-29 | TSLA | long | squeeze | TSLA260629C00400000 | 11:28 | 1.52 | 11:41 | 1.71 | trailing_stop | $+18.83 |
| 15 | 2026-06-30 | QQQ | long | squeeze | QQQ260630C00734000 | 11:35 | 1.49 | 12:00 | 1.63 | noon_shutdown | $+13.76 |
| 16 | 2026-07-01 | TSLA | long | squeeze | TSLA260701C00430000 | 10:48 | 1.78 | 10:54 | 1.50 | trailing_stop | $-28.27 |
| 17 | 2026-07-07 | QQQ | long | squeeze | QQQ260707C00708000 | 11:45 | 1.73 | 12:00 | 2.40 | noon_shutdown | $+66.70 |
| 18 | 2026-07-08 | TSLA | long | squeeze | TSLA260708C00397500 | 10:22 | 1.98 | 10:27 | 1.96 | trailing_stop | $-2.37 |
| 19 | 2026-07-10 | TSLA | long | squeeze | TSLA260710C00410000 | 11:17 | 1.42 | 11:38 | 1.68 | trailing_stop | $+26.29 |
| 20 | 2026-07-13 | TSLA | short | squeeze | TSLA260713P00392500 | 10:17 | 1.95 | 10:20 | 1.69 | trailing_stop | $-26.06 |
| 21 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.49 | 11:49 | 2.74 | volume_faded | $+25.52 |
| 22 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:18 | 4.17 | volume_faded | $+40.08 |
| 23 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:58 | 1.56 | trailing_stop | $-38.08 |
| 24 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.86 | 11:27 | 1.81 | volume_faded | $-4.34 |
| 25 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.84 | 11:42 | 3.15 | volume_faded | $+31.02 |
| 26 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.62 | 10:11 | 2.63 | volume_faded | $+0.50 |
| 27 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.83 | 10:36 | 2.84 | volume_faded | $+1.66 |
| 28 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:46 | 3.59 | trailing_stop | $+149.34 |
| 29 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:22 | 2.47 | volume_faded | $-58.02 |
| 30 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:20 | 3.11 | volume_faded | $+0.58 |
| 31 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.41 | 11:17 | 1.65 | trailing_stop | $-75.59 |
| 32 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.98 | 10:46 | 1.85 | volume_faded | $-12.66 |
| 33 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 11:00 | 1.34 | trailing_stop | $-18.54 |
| 34 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.91 | 10:22 | 1.94 | volume_faded | $+3.30 |
| 35 | 2026-08-10 | TSLA | long | squeeze | TSLA260810C00332500 | 10:27 | 1.11 | 10:36 | 0.94 | trailing_stop | $-17.10 |
| 36 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.59 | 11:24 | 1.27 | setup_failed | $-31.72 |
| 37 | 2026-08-11 | QQQ | long | pullback | QQQ260811C00721000 | 10:12 | 2.02 | 10:13 | 1.98 | volume_faded | $-4.00 |
| 38 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.92 | 10:41 | 1.45 | trailing_stop | $+53.63 |
| 39 | 2026-08-13 | QQQ | long | pullback | QQQ260813C00732000 | 11:14 | 1.88 | 11:15 | 1.67 | volume_faded | $-21.08 |
| 40 | 2026-08-17 | TSLA | long | pullback | TSLA260817C00337500 | 10:36 | 3.20 | 10:37 | 3.38 | volume_faded | $+17.82 |
| 41 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.87 | 10:12 | 2.11 | volume_faded | $+24.04 |
| 42 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.75 | 10:42 | 2.50 | volume_faded | $-25.50 |
| 43 | 2026-08-19 | META | long | squeeze | META260819C00550000 | 10:47 | 1.96 | 11:02 | 1.80 | trailing_stop | $-16.11 |
| 44 | 2026-08-21 | META | long | pullback | META260821C00550000 | 10:09 | 3.31 | 10:10 | 3.33 | volume_faded | $+1.70 |
| 45 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.68 | 11:07 | 2.06 | trailing_stop | $+38.19 |
| 46 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.85 | 11:29 | 0.58 | trailing_stop | $-26.58 |
| 47 | 2026-08-25 | QQQ | short | pullback | QQQ260825P00710000 | 11:02 | 1.74 | 11:03 | 1.69 | volume_faded | $-5.86 |
| 48 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 2.01 | 10:21 | 1.44 | trailing_stop | $-56.88 |
| 49 | 2026-08-27 | QQQ | long | pullback | QQQ260827C00717000 | 10:08 | 2.12 | 10:09 | 1.82 | volume_faded | $-29.88 |
| 50 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.47 | 10:48 | 1.03 | trailing_stop | $-43.98 |
| 51 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.18 | 10:43 | 0.84 | trailing_stop | $-34.63 |
| 52 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.39 | 10:20 | 1.93 | trailing_stop | $-45.23 |
| 53 | 2026-08-31 | TSLA | long | pullback | TSLA260831C00362500 | 11:44 | 3.26 | 11:48 | 3.97 | volume_faded | $+70.50 |
| 54 | 2026-09-01 | QQQ | long | pullback | QQQ260901C00708000 | 10:16 | 1.74 | 10:17 | 1.57 | volume_faded | $-17.62 |
| 55 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.23 | 12:00 | 4.69 | noon_shutdown | $+346.00 |
| 56 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 1.81 | trailing_stop | $-49.79 |
| 57 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 11:21 | 1.37 | trailing_stop | $+43.36 |
| 58 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:28 | 1.13 | volume_faded | $-17.86 |
| 59 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:38 | 1.21 | trailing_stop | $-28.18 |
| 60 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.55 | 11:37 | 1.77 | volume_faded | $+22.34 |
| 61 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.13 | 10:18 | 2.31 | volume_faded | $+18.10 |
| 62 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 11:03 | 2.94 | trailing_stop | $+168.15 |
| 63 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.30 | 11:15 | 1.12 | setup_failed | $-17.82 |
| 64 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.68 | 11:34 | 1.40 | setup_failed | $-28.16 |
| 65 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.80 | 10:15 | 1.97 | volume_faded | $+17.46 |
| 66 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 11:02 | 2.33 | trailing_stop | $-95.20 |
| 67 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:59 | 2.26 | trailing_stop | $-45.96 |
| 68 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 12:00 | 5.93 | noon_shutdown | $+246.10 |
| 69 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.23 | 10:44 | 3.65 | setup_failed | $-58.74 |
| 70 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 4.05 | 11:22 | 3.48 | volume_faded | $-57.04 |
| 71 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.49 | trailing_stop | $-68.22 |
| 72 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:54 | 1.43 | trailing_stop | $-34.79 |
| 73 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00742000 | 11:20 | 1.24 | 11:22 | 1.22 | volume_faded | $-2.92 |
| 74 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.66 | 10:08 | 5.24 | volume_faded | $-41.80 |
| 75 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:17 | 2.55 | trailing_stop | $-8.99 |
| 76 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 12:00 | 3.38 | noon_shutdown | $+76.98 |
| 77 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:01 | 3.22 | trailing_stop | $+2.14 |
| 78 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.93 | 11:48 | 3.41 | setup_failed | $-51.66 |
| 79 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 11:41 | 4.63 | trailing_stop | $+135.63 |
| 80 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.25 | 11:47 | 2.00 | volume_faded | $-25.50 |
| 81 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 4.03 | 10:42 | 4.21 | volume_faded | $+18.50 |
| 82 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.52 | 10:51 | 4.04 | volume_faded | $-48.10 |
| 83 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:50 | 2.26 | trailing_stop | $-81.66 |

## atr/v4_no_bar_exits

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 82 | 31.7% | $+64.28 | $-35.37 | $-309.53 | $-3.77 | $+346.00 | $-96.24 | $+346.00 | $-234.60 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 35 | 40.0% | $+273.97 | $+7.83 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| QQQ | 28 | 14.3% | $-251.15 | $-8.97 |
| META | 18 | 44.4% | $-296.00 | $-16.44 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 5 | 100.0% | $+679.32 | $+135.86 |
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| time_stop | 4 | 100.0% | $+214.36 | $+53.59 |
| hard_stop | 9 | 0.0% | $-503.54 | $-55.95 |
| trailing_stop | 63 | 25.4% | $-1,045.67 | $-16.60 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 43 | 27.9% | $+62.30 | $+1.45 |
| short | 39 | 35.9% | $-371.83 | $-9.53 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.68 | 10:13 | 1.32 | hard_stop | $-36.35 |
| 2 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.42 | 10:46 | 2.74 | trailing_stop | $+32.66 |
| 3 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 6.01 | 10:52 | 5.30 | trailing_stop | $-70.89 |
| 4 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 10:34 | 3.21 | 10:44 | 3.15 | trailing_stop | $-6.43 |
| 5 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 11:47 | 2.92 | 11:48 | 2.28 | hard_stop | $-63.38 |
| 6 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.59 | 10:59 | 2.46 | trailing_stop | $-13.10 |
| 7 | 2026-06-22 | TSLA | long | pullback | TSLA260622C00410000 | 11:44 | 2.61 | 11:46 | 2.05 | hard_stop | $-56.40 |
| 8 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.11 | 11:55 | 1.66 | trailing_stop | $-45.61 |
| 9 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.48 | 11:19 | 1.32 | trailing_stop | $-16.19 |
| 10 | 2026-06-26 | TSLA | long | pullback | TSLA260626C00372500 | 09:52 | 3.06 | 10:00 | 4.50 | profit_target | $+143.82 |
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
| 21 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.49 | 11:54 | 2.67 | trailing_stop | $+17.68 |
| 22 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:23 | 5.55 | profit_target | $+177.38 |
| 23 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:57 | 1.78 | trailing_stop | $-15.83 |
| 24 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.86 | 11:28 | 1.64 | trailing_stop | $-21.91 |
| 25 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.84 | 11:46 | 3.53 | time_stop | $+69.24 |
| 26 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.62 | 10:13 | 2.31 | trailing_stop | $-30.93 |
| 27 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.83 | 10:37 | 2.49 | trailing_stop | $-33.34 |
| 28 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:31 | 2.29 | trailing_stop | $+18.81 |
| 29 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:21 | 2.39 | trailing_stop | $-65.88 |
| 30 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:21 | 2.73 | trailing_stop | $-36.59 |
| 31 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.41 | 11:16 | 1.89 | hard_stop | $-52.00 |
| 32 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.98 | 10:55 | 1.55 | trailing_stop | $-42.74 |
| 33 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 10:58 | 1.54 | trailing_stop | $+0.66 |
| 34 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.91 | 10:33 | 2.24 | trailing_stop | $+33.57 |
| 35 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.59 | 11:25 | 1.25 | trailing_stop | $-34.37 |
| 36 | 2026-08-11 | QQQ | long | pullback | QQQ260811C00721000 | 10:12 | 2.02 | 10:39 | 1.41 | trailing_stop | $-60.84 |
| 37 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.92 | 10:37 | 1.66 | trailing_stop | $+74.41 |
| 38 | 2026-08-13 | QQQ | long | pullback | QQQ260813C00732000 | 11:14 | 1.88 | 11:18 | 1.47 | hard_stop | $-40.54 |
| 39 | 2026-08-17 | TSLA | long | pullback | TSLA260817C00337500 | 10:36 | 3.20 | 10:46 | 3.52 | time_stop | $+31.54 |
| 40 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.87 | 10:15 | 1.65 | trailing_stop | $-22.03 |
| 41 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.75 | 10:51 | 3.66 | time_stop | $+90.14 |
| 42 | 2026-08-21 | META | long | pullback | META260821C00550000 | 10:09 | 3.31 | 10:13 | 2.92 | trailing_stop | $-39.12 |
| 43 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.68 | 10:58 | 2.04 | trailing_stop | $+35.54 |
| 44 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.85 | 11:29 | 0.66 | trailing_stop | $-18.29 |
| 45 | 2026-08-25 | QQQ | short | pullback | QQQ260825P00710000 | 11:02 | 1.74 | 11:11 | 1.37 | trailing_stop | $-37.67 |
| 46 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 2.01 | 10:20 | 1.65 | trailing_stop | $-36.30 |
| 47 | 2026-08-27 | QQQ | long | pullback | QQQ260827C00717000 | 10:08 | 2.12 | 10:08 | 1.66 | hard_stop | $-45.83 |
| 48 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.47 | 10:42 | 1.15 | trailing_stop | $-31.73 |
| 49 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.18 | 10:41 | 0.96 | trailing_stop | $-22.67 |
| 50 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.39 | 10:18 | 2.21 | trailing_stop | $-17.59 |
| 51 | 2026-08-31 | TSLA | long | pullback | TSLA260831C00362500 | 11:44 | 3.26 | 11:51 | 4.80 | profit_target | $+153.41 |
| 52 | 2026-09-01 | QQQ | long | pullback | QQQ260901C00708000 | 10:16 | 1.74 | 10:18 | 1.54 | trailing_stop | $-20.58 |
| 53 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.23 | 12:00 | 4.69 | noon_shutdown | $+346.00 |
| 54 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 55 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 10:52 | 0.78 | trailing_stop | $-16.22 |
| 56 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.95 | 10:58 | 0.87 | trailing_stop | $-7.84 |
| 57 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:32 | 1.02 | trailing_stop | $-28.20 |
| 58 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:37 | 1.38 | trailing_stop | $-10.94 |
| 59 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.55 | 11:38 | 1.52 | trailing_stop | $-3.10 |
| 60 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.13 | 10:20 | 2.30 | trailing_stop | $+16.63 |
| 61 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 10:18 | 1.59 | trailing_stop | $+33.69 |
| 62 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.30 | 11:16 | 1.02 | hard_stop | $-27.98 |
| 63 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.68 | 11:36 | 1.32 | trailing_stop | $-36.35 |
| 64 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.80 | 10:18 | 1.58 | trailing_stop | $-21.18 |
| 65 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 10:57 | 2.63 | trailing_stop | $-65.80 |
| 66 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:49 | 2.27 | trailing_stop | $-44.98 |
| 67 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 11:37 | 3.53 | trailing_stop | $+6.00 |
| 68 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.23 | 10:49 | 3.32 | trailing_stop | $-91.43 |
| 69 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 4.05 | 11:22 | 3.09 | hard_stop | $-96.24 |
| 70 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.70 | trailing_stop | $-46.93 |
| 71 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:53 | 1.63 | trailing_stop | $-14.41 |
| 72 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00742000 | 11:20 | 1.24 | 11:28 | 1.83 | profit_target | $+58.49 |
| 73 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.66 | 10:10 | 6.10 | trailing_stop | $+43.46 |
| 74 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:13 | 2.90 | trailing_stop | $+25.90 |
| 75 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 11:40 | 2.69 | trailing_stop | $+7.40 |
| 76 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 77 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.93 | 11:48 | 3.08 | hard_stop | $-84.82 |
| 78 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 10:44 | 3.21 | trailing_stop | $-5.98 |
| 79 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.25 | 11:50 | 1.77 | trailing_stop | $-48.69 |
| 80 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 4.03 | 10:45 | 3.55 | trailing_stop | $-47.54 |
| 81 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.52 | 10:59 | 4.75 | time_stop | $+23.44 |
| 82 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:24 | 2.56 | trailing_stop | $-52.26 |

## spy/baseline

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 64 | 25.0% | $+31.85 | $-17.62 | $-336.09 | $-5.25 | $+102.59 | $-48.03 | $+102.59 | $-76.62 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 64 | 25.0% | $-336.09 | $-5.25 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 2 | 100.0% | $+204.22 | $+102.11 |
| hard_stop | 2 | 0.0% | $-65.88 | $-32.94 |
| volume_faded | 25 | 20.0% | $-148.00 | $-5.92 |
| trailing_stop | 27 | 33.3% | $-160.47 | $-5.94 |
| setup_failed | 8 | 0.0% | $-165.96 | $-20.75 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 32 | 21.9% | $-136.12 | $-4.25 |
| long | 32 | 28.1% | $-199.97 | $-6.25 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-03 | SPY | short | pullback | SPY260603P00757000 | 11:15 | 1.81 | 11:16 | 1.65 | setup_failed | $-15.90 |
| 2 | 2026-06-03 | SPY | short | pullback | SPY260603P00756000 | 11:35 | 1.40 | 11:36 | 1.31 | volume_faded | $-8.42 |
| 3 | 2026-06-04 | SPY | long | squeeze | SPY260604C00755000 | 11:01 | 0.87 | 11:20 | 1.28 | trailing_stop | $+41.09 |
| 4 | 2026-06-12 | SPY | short | squeeze | SPY260612P00738000 | 10:44 | 2.78 | 10:50 | 2.54 | trailing_stop | $-24.44 |
| 5 | 2026-06-15 | SPY | long | squeeze | SPY260615C00754000 | 10:49 | 1.11 | 11:34 | 1.51 | trailing_stop | $+40.13 |
| 6 | 2026-06-22 | SPY | short | pullback | SPY260622P00745000 | 11:20 | 1.93 | 11:22 | 1.77 | volume_faded | $-15.40 |
| 7 | 2026-06-23 | SPY | short | pullback | SPY260623P00735000 | 11:39 | 1.94 | 11:40 | 1.88 | volume_faded | $-5.64 |
| 8 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:18 | 1.70 | 11:19 | 1.59 | volume_faded | $-11.58 |
| 9 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:30 | 1.88 | 11:31 | 1.58 | volume_faded | $-29.90 |
| 10 | 2026-06-25 | SPY | short | pullback | SPY260625P00737000 | 09:40 | 2.18 | 09:42 | 3.21 | profit_target | $+102.59 |
| 11 | 2026-07-02 | SPY | short | pullback | SPY260702P00747000 | 11:05 | 2.16 | 11:07 | 3.18 | profit_target | $+101.63 |
| 12 | 2026-07-06 | SPY | long | pullback | SPY260706C00750000 | 10:54 | 0.89 | 10:55 | 0.78 | volume_faded | $-10.34 |
| 13 | 2026-07-07 | SPY | long | squeeze | SPY260707C00747000 | 11:45 | 0.80 | 11:49 | 0.93 | trailing_stop | $+12.95 |
| 14 | 2026-07-08 | SPY | short | squeeze | SPY260708P00741000 | 11:15 | 1.59 | 11:19 | 1.54 | trailing_stop | $-5.46 |
| 15 | 2026-07-08 | SPY | short | pullback | SPY260708P00741000 | 11:23 | 1.81 | 11:28 | 2.19 | volume_faded | $+38.00 |
| 16 | 2026-07-09 | SPY | short | pullback | SPY260709P00748000 | 10:53 | 1.64 | 10:54 | 1.29 | trailing_stop | $-35.47 |
| 17 | 2026-07-10 | SPY | short | squeeze | SPY260710P00749000 | 10:33 | 1.30 | 10:33 | 1.02 | trailing_stop | $-27.98 |
| 18 | 2026-07-10 | SPY | short | squeeze | SPY260710P00750000 | 10:34 | 1.31 | 10:34 | 1.02 | trailing_stop | $-28.20 |
| 19 | 2026-07-13 | SPY | short | pullback | SPY260713P00752000 | 10:54 | 1.30 | 10:55 | 1.07 | setup_failed | $-22.72 |
| 20 | 2026-07-16 | SPY | long | pullback | SPY260716C00754000 | 10:45 | 1.35 | 10:46 | 1.26 | volume_faded | $-8.22 |
| 21 | 2026-07-17 | SPY | long | pullback | SPY260717C00745000 | 11:47 | 1.63 | 11:48 | 1.47 | setup_failed | $-16.20 |
| 22 | 2026-07-21 | SPY | long | squeeze | SPY260721C00747000 | 10:19 | 0.83 | 10:21 | 0.68 | trailing_stop | $-14.41 |
| 23 | 2026-07-23 | SPY | short | pullback | SPY260723P00740000 | 10:20 | 2.17 | 10:21 | 1.74 | setup_failed | $-42.82 |
| 24 | 2026-07-23 | SPY | short | pullback | SPY260723P00737000 | 11:23 | 2.12 | 11:24 | 1.78 | volume_faded | $-33.80 |
| 25 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:11 | 1.75 | 11:11 | 1.81 | trailing_stop | $+5.86 |
| 26 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:12 | 1.91 | 11:13 | 1.74 | volume_faded | $-16.30 |
| 27 | 2026-07-28 | SPY | short | pullback | SPY260728P00737000 | 10:15 | 2.02 | 10:16 | 1.96 | volume_faded | $-5.96 |
| 28 | 2026-07-31 | SPY | long | pullback | SPY260731C00742000 | 11:16 | 1.87 | 11:16 | 1.46 | hard_stop | $-40.32 |
| 29 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:17 | 0.97 | 11:18 | 0.95 | volume_faded | $-1.84 |
| 30 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:34 | 1.06 | 11:35 | 1.00 | volume_faded | $-6.12 |
| 31 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:38 | 1.04 | 11:40 | 1.19 | volume_faded | $+14.54 |
| 32 | 2026-08-05 | SPY | short | squeeze | SPY260805P00772000 | 10:54 | 1.49 | 10:57 | 1.18 | trailing_stop | $-30.54 |
| 33 | 2026-08-05 | SPY | short | squeeze | SPY260805P00771000 | 11:50 | 1.37 | 11:58 | 1.43 | trailing_stop | $+6.79 |
| 34 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 09:58 | 1.31 | 09:59 | 1.37 | volume_faded | $+6.64 |
| 35 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 10:30 | 1.40 | 10:31 | 1.18 | setup_failed | $-22.14 |
| 36 | 2026-08-18 | SPY | long | pullback | SPY260818C00768000 | 10:36 | 1.74 | 10:37 | 1.66 | volume_faded | $-8.80 |
| 37 | 2026-08-20 | SPY | long | pullback | SPY260820C00767000 | 11:01 | 1.29 | 11:03 | 1.51 | trailing_stop | $+22.62 |
| 38 | 2026-08-20 | SPY | short | pullback | SPY260820P00766000 | 11:36 | 1.16 | 11:37 | 1.03 | volume_faded | $-13.38 |
| 39 | 2026-08-21 | SPY | short | pullback | SPY260821P00765000 | 10:20 | 1.29 | 10:21 | 1.19 | volume_faded | $-9.94 |
| 40 | 2026-08-24 | SPY | long | pullback | SPY260824C00763000 | 10:22 | 1.21 | 10:23 | 1.04 | setup_failed | $-17.50 |
| 41 | 2026-08-25 | SPY | long | pullback | SPY260825C00765000 | 11:29 | 0.92 | 11:32 | 0.82 | setup_failed | $-9.48 |
| 42 | 2026-08-27 | SPY | long | squeeze | SPY260827C00771000 | 10:50 | 0.69 | 10:53 | 0.59 | trailing_stop | $-10.56 |
| 43 | 2026-09-08 | SPY | short | pullback | SPY260908P00768000 | 11:23 | 1.18 | 11:24 | 0.93 | hard_stop | $-25.56 |
| 44 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 10:17 | 1.03 | 10:25 | 1.07 | trailing_stop | $+4.39 |
| 45 | 2026-09-09 | SPY | long | squeeze | SPY260909C00765000 | 11:01 | 0.67 | 11:01 | 0.53 | trailing_stop | $-14.54 |
| 46 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 11:02 | 0.90 | 11:16 | 1.63 | trailing_stop | $+73.31 |
| 47 | 2026-09-10 | SPY | long | pullback | SPY260910C00759000 | 10:58 | 1.44 | 10:59 | 1.34 | volume_faded | $-9.56 |
| 48 | 2026-09-14 | SPY | long | pullback | SPY260914C00760000 | 10:02 | 1.52 | 10:03 | 1.27 | volume_faded | $-24.58 |
| 49 | 2026-09-15 | SPY | long | squeeze | SPY260915C00758000 | 11:43 | 0.81 | 11:46 | 0.64 | trailing_stop | $-17.08 |
| 50 | 2026-09-18 | SPY | short | squeeze | SPY260918P00758000 | 10:44 | 0.77 | 10:46 | 0.61 | trailing_stop | $-15.35 |
| 51 | 2026-09-18 | SPY | long | squeeze | SPY260918C00760000 | 10:51 | 0.88 | 11:02 | 0.82 | trailing_stop | $-5.40 |
| 52 | 2026-09-22 | SPY | short | pullback | SPY260922P00774000 | 10:40 | 1.31 | 10:42 | 1.51 | volume_faded | $+20.36 |
| 53 | 2026-09-22 | SPY | short | squeeze | SPY260922P00773000 | 10:43 | 1.03 | 10:44 | 0.81 | trailing_stop | $-22.25 |
| 54 | 2026-09-25 | SPY | long | pullback | SPY260925C00769000 | 11:31 | 1.26 | 11:33 | 1.39 | volume_faded | $+12.68 |
| 55 | 2026-10-01 | SPY | short | pullback | SPY261001P00760000 | 11:44 | 1.64 | 11:45 | 1.49 | volume_faded | $-15.26 |
| 56 | 2026-10-05 | SPY | short | squeeze | SPY261005P00770000 | 10:01 | 1.19 | 10:01 | 0.94 | trailing_stop | $-25.78 |
| 57 | 2026-10-05 | SPY | long | pullback | SPY261005C00772000 | 11:24 | 1.31 | 11:25 | 1.30 | volume_faded | $-0.22 |
| 58 | 2026-10-12 | SPY | short | pullback | SPY261012P00779000 | 11:24 | 1.26 | 11:25 | 1.22 | volume_faded | $-4.96 |
| 59 | 2026-10-14 | SPY | long | squeeze | SPY261014C00774000 | 10:35 | 0.91 | 10:36 | 0.71 | trailing_stop | $-19.44 |
| 60 | 2026-10-14 | SPY | short | squeeze | SPY261014P00772000 | 10:38 | 1.03 | 10:40 | 0.90 | trailing_stop | $-12.86 |
| 61 | 2026-10-21 | SPY | long | pullback | SPY261021C00770000 | 09:42 | 2.22 | 09:43 | 1.74 | trailing_stop | $-48.03 |
| 62 | 2026-10-22 | SPY | short | pullback | SPY261022P00763000 | 11:15 | 1.90 | 11:16 | 1.71 | setup_failed | $-19.20 |
| 63 | 2026-10-22 | SPY | long | squeeze | SPY261022C00764000 | 11:18 | 1.50 | 11:27 | 1.56 | trailing_stop | $+6.08 |
| 64 | 2026-10-23 | SPY | short | squeeze | SPY261023P00759000 | 10:17 | 1.81 | 10:21 | 1.65 | trailing_stop | $-15.90 |

## spy/v0_no_slippage

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 64 | 32.8% | $+28.70 | $-14.27 | $-10.80 | $-0.17 | $+107.00 | $-43.60 | $+107.00 | $-61.00 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 64 | 32.8% | $-10.80 | $-0.17 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 2 | 100.0% | $+213.00 | $+106.50 |
| volume_faded | 25 | 36.0% | $-2.00 | $-0.08 |
| hard_stop | 1 | 0.0% | $-36.60 | $-36.60 |
| trailing_stop | 27 | 37.0% | $-38.20 | $-1.41 |
| setup_failed | 9 | 0.0% | $-147.00 | $-16.33 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 32 | 31.2% | $+40.80 | $+1.27 |
| long | 32 | 34.4% | $-51.60 | $-1.61 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-03 | SPY | short | pullback | SPY260603P00757000 | 11:15 | 1.77 | 11:16 | 1.68 | setup_failed | $-9.00 |
| 2 | 2026-06-03 | SPY | short | pullback | SPY260603P00756000 | 11:35 | 1.37 | 11:36 | 1.34 | volume_faded | $-3.00 |
| 3 | 2026-06-04 | SPY | long | squeeze | SPY260604C00755000 | 11:01 | 0.85 | 11:20 | 1.30 | trailing_stop | $+45.40 |
| 4 | 2026-06-12 | SPY | short | squeeze | SPY260612P00738000 | 10:44 | 2.73 | 10:50 | 2.59 | trailing_stop | $-13.80 |
| 5 | 2026-06-15 | SPY | long | squeeze | SPY260615C00754000 | 10:49 | 1.09 | 11:34 | 1.54 | trailing_stop | $+45.40 |
| 6 | 2026-06-22 | SPY | short | pullback | SPY260622P00745000 | 11:20 | 1.89 | 11:22 | 1.81 | volume_faded | $-8.00 |
| 7 | 2026-06-23 | SPY | short | pullback | SPY260623P00735000 | 11:39 | 1.90 | 11:40 | 1.92 | volume_faded | $+2.00 |
| 8 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:18 | 1.67 | 11:19 | 1.62 | volume_faded | $-5.00 |
| 9 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:30 | 1.84 | 11:31 | 1.61 | volume_faded | $-23.00 |
| 10 | 2026-06-25 | SPY | short | pullback | SPY260625P00737000 | 09:40 | 2.14 | 09:42 | 3.21 | profit_target | $+107.00 |
| 11 | 2026-07-02 | SPY | short | pullback | SPY260702P00747000 | 11:05 | 2.12 | 11:07 | 3.18 | profit_target | $+106.00 |
| 12 | 2026-07-06 | SPY | long | pullback | SPY260706C00750000 | 10:54 | 0.87 | 10:55 | 0.80 | volume_faded | $-7.00 |
| 13 | 2026-07-07 | SPY | long | squeeze | SPY260707C00747000 | 11:45 | 0.78 | 11:49 | 0.94 | trailing_stop | $+16.40 |
| 14 | 2026-07-08 | SPY | short | squeeze | SPY260708P00741000 | 11:15 | 1.56 | 11:19 | 1.57 | trailing_stop | $+0.80 |
| 15 | 2026-07-08 | SPY | short | pullback | SPY260708P00741000 | 11:23 | 1.77 | 11:28 | 2.23 | volume_faded | $+46.00 |
| 16 | 2026-07-09 | SPY | short | pullback | SPY260709P00748000 | 10:53 | 1.61 | 10:54 | 1.34 | setup_failed | $-27.00 |
| 17 | 2026-07-10 | SPY | short | squeeze | SPY260710P00749000 | 10:33 | 1.27 | 10:33 | 1.02 | trailing_stop | $-25.40 |
| 18 | 2026-07-10 | SPY | short | squeeze | SPY260710P00750000 | 10:34 | 1.28 | 10:34 | 1.02 | trailing_stop | $-25.60 |
| 19 | 2026-07-13 | SPY | short | pullback | SPY260713P00752000 | 10:54 | 1.27 | 10:55 | 1.09 | setup_failed | $-18.00 |
| 20 | 2026-07-16 | SPY | long | pullback | SPY260716C00754000 | 10:45 | 1.32 | 10:46 | 1.29 | volume_faded | $-3.00 |
| 21 | 2026-07-17 | SPY | long | pullback | SPY260717C00745000 | 11:47 | 1.60 | 11:48 | 1.50 | setup_failed | $-10.00 |
| 22 | 2026-07-21 | SPY | long | squeeze | SPY260721C00747000 | 10:19 | 0.81 | 10:21 | 0.70 | trailing_stop | $-11.40 |
| 23 | 2026-07-23 | SPY | short | pullback | SPY260723P00740000 | 10:20 | 2.13 | 10:21 | 1.78 | setup_failed | $-35.00 |
| 24 | 2026-07-23 | SPY | short | pullback | SPY260723P00737000 | 11:23 | 2.08 | 11:24 | 1.82 | volume_faded | $-26.00 |
| 25 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:11 | 1.72 | 11:11 | 1.85 | trailing_stop | $+13.00 |
| 26 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:12 | 1.87 | 11:13 | 1.78 | volume_faded | $-9.00 |
| 27 | 2026-07-28 | SPY | short | pullback | SPY260728P00737000 | 10:15 | 1.98 | 10:16 | 2.00 | volume_faded | $+2.00 |
| 28 | 2026-07-31 | SPY | long | pullback | SPY260731C00742000 | 11:16 | 1.83 | 11:16 | 1.46 | hard_stop | $-36.60 |
| 29 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:17 | 0.95 | 11:18 | 0.97 | volume_faded | $+2.00 |
| 30 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:34 | 1.04 | 11:35 | 1.02 | volume_faded | $-2.00 |
| 31 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:38 | 1.02 | 11:40 | 1.21 | volume_faded | $+19.00 |
| 32 | 2026-08-05 | SPY | short | squeeze | SPY260805P00772000 | 10:54 | 1.46 | 10:57 | 1.21 | trailing_stop | $-25.20 |
| 33 | 2026-08-05 | SPY | short | squeeze | SPY260805P00771000 | 11:50 | 1.34 | 11:58 | 1.46 | trailing_stop | $+12.40 |
| 34 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 09:58 | 1.28 | 09:59 | 1.40 | volume_faded | $+12.00 |
| 35 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 10:30 | 1.37 | 10:31 | 1.20 | setup_failed | $-17.00 |
| 36 | 2026-08-18 | SPY | long | pullback | SPY260818C00768000 | 10:36 | 1.71 | 10:37 | 1.69 | volume_faded | $-2.00 |
| 37 | 2026-08-20 | SPY | long | pullback | SPY260820C00767000 | 11:01 | 1.26 | 11:03 | 1.51 | trailing_stop | $+25.20 |
| 38 | 2026-08-20 | SPY | short | pullback | SPY260820P00766000 | 11:36 | 1.14 | 11:37 | 1.05 | volume_faded | $-9.00 |
| 39 | 2026-08-21 | SPY | short | pullback | SPY260821P00765000 | 10:20 | 1.26 | 10:21 | 1.21 | volume_faded | $-5.00 |
| 40 | 2026-08-24 | SPY | long | pullback | SPY260824C00763000 | 10:22 | 1.19 | 10:23 | 1.06 | setup_failed | $-13.00 |
| 41 | 2026-08-25 | SPY | long | pullback | SPY260825C00765000 | 11:29 | 0.90 | 11:32 | 0.84 | setup_failed | $-6.00 |
| 42 | 2026-08-27 | SPY | long | squeeze | SPY260827C00771000 | 10:50 | 0.68 | 10:53 | 0.60 | trailing_stop | $-8.00 |
| 43 | 2026-09-08 | SPY | short | pullback | SPY260908P00768000 | 11:23 | 1.16 | 11:24 | 0.93 | trailing_stop | $-23.20 |
| 44 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 10:17 | 1.01 | 10:25 | 1.10 | trailing_stop | $+8.60 |
| 45 | 2026-09-09 | SPY | long | squeeze | SPY260909C00765000 | 11:01 | 0.66 | 11:01 | 0.53 | trailing_stop | $-13.20 |
| 46 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 11:02 | 0.88 | 11:16 | 1.66 | trailing_stop | $+78.40 |
| 47 | 2026-09-10 | SPY | long | pullback | SPY260910C00759000 | 10:58 | 1.41 | 10:59 | 1.37 | volume_faded | $-4.00 |
| 48 | 2026-09-14 | SPY | long | pullback | SPY260914C00760000 | 10:02 | 1.49 | 10:03 | 1.30 | volume_faded | $-19.00 |
| 49 | 2026-09-15 | SPY | long | squeeze | SPY260915C00758000 | 11:43 | 0.79 | 11:46 | 0.65 | trailing_stop | $-14.20 |
| 50 | 2026-09-18 | SPY | short | squeeze | SPY260918P00758000 | 10:44 | 0.75 | 10:46 | 0.62 | trailing_stop | $-12.60 |
| 51 | 2026-09-18 | SPY | long | squeeze | SPY260918C00760000 | 10:51 | 0.86 | 11:02 | 0.84 | trailing_stop | $-2.00 |
| 52 | 2026-09-22 | SPY | short | pullback | SPY260922P00774000 | 10:40 | 1.28 | 10:42 | 1.54 | volume_faded | $+26.00 |
| 53 | 2026-09-22 | SPY | short | squeeze | SPY260922P00773000 | 10:43 | 1.01 | 10:44 | 0.81 | trailing_stop | $-20.20 |
| 54 | 2026-09-25 | SPY | long | pullback | SPY260925C00769000 | 11:31 | 1.24 | 11:33 | 1.42 | volume_faded | $+18.00 |
| 55 | 2026-10-01 | SPY | short | pullback | SPY261001P00760000 | 11:44 | 1.61 | 11:45 | 1.52 | volume_faded | $-9.00 |
| 56 | 2026-10-05 | SPY | short | squeeze | SPY261005P00770000 | 10:01 | 1.17 | 10:01 | 0.94 | trailing_stop | $-23.40 |
| 57 | 2026-10-05 | SPY | long | pullback | SPY261005C00772000 | 11:24 | 1.28 | 11:25 | 1.33 | volume_faded | $+5.00 |
| 58 | 2026-10-12 | SPY | short | pullback | SPY261012P00779000 | 11:24 | 1.24 | 11:25 | 1.24 | volume_faded | $+0.00 |
| 59 | 2026-10-14 | SPY | long | squeeze | SPY261014C00774000 | 10:35 | 0.89 | 10:36 | 0.73 | trailing_stop | $-16.20 |
| 60 | 2026-10-14 | SPY | short | squeeze | SPY261014P00772000 | 10:38 | 1.01 | 10:40 | 0.92 | trailing_stop | $-9.00 |
| 61 | 2026-10-21 | SPY | long | pullback | SPY261021C00770000 | 09:42 | 2.18 | 09:43 | 1.74 | trailing_stop | $-43.60 |
| 62 | 2026-10-22 | SPY | short | pullback | SPY261022P00763000 | 11:15 | 1.86 | 11:16 | 1.74 | setup_failed | $-12.00 |
| 63 | 2026-10-22 | SPY | long | squeeze | SPY261022C00764000 | 11:18 | 1.47 | 11:27 | 1.59 | trailing_stop | $+12.20 |
| 64 | 2026-10-23 | SPY | short | squeeze | SPY261023P00759000 | 10:17 | 1.77 | 10:21 | 1.68 | trailing_stop | $-9.00 |

## spy/v1_volume_fade_3

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 62 | 30.6% | $+31.78 | $-21.37 | $-314.92 | $-5.08 | $+102.59 | $-48.03 | $+102.59 | $-63.88 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 62 | 30.6% | $-314.92 | $-5.08 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 3 | 100.0% | $+293.87 | $+97.96 |
| volume_faded | 13 | 38.5% | $-46.50 | $-3.58 |
| hard_stop | 3 | 0.0% | $-96.95 | $-32.32 |
| setup_failed | 9 | 0.0% | $-207.20 | $-23.02 |
| trailing_stop | 34 | 32.4% | $-258.14 | $-7.59 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 31 | 32.3% | $-119.66 | $-3.86 |
| short | 31 | 29.0% | $-195.26 | $-6.30 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-03 | SPY | short | pullback | SPY260603P00757000 | 11:15 | 1.81 | 11:16 | 1.65 | setup_failed | $-15.90 |
| 2 | 2026-06-03 | SPY | short | pullback | SPY260603P00756000 | 11:35 | 1.40 | 11:38 | 1.53 | volume_faded | $+13.14 |
| 3 | 2026-06-04 | SPY | long | squeeze | SPY260604C00755000 | 11:01 | 0.87 | 11:20 | 1.28 | trailing_stop | $+41.09 |
| 4 | 2026-06-12 | SPY | short | squeeze | SPY260612P00738000 | 10:44 | 2.78 | 10:50 | 2.54 | trailing_stop | $-24.44 |
| 5 | 2026-06-15 | SPY | long | squeeze | SPY260615C00754000 | 10:49 | 1.11 | 11:34 | 1.51 | trailing_stop | $+40.13 |
| 6 | 2026-06-22 | SPY | short | pullback | SPY260622P00745000 | 11:20 | 1.93 | 11:23 | 1.51 | trailing_stop | $-41.64 |
| 7 | 2026-06-23 | SPY | short | pullback | SPY260623P00735000 | 11:39 | 1.94 | 11:42 | 1.69 | volume_faded | $-25.24 |
| 8 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:18 | 1.70 | 11:21 | 1.47 | volume_faded | $-23.34 |
| 9 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:30 | 1.88 | 11:33 | 1.47 | trailing_stop | $-40.54 |
| 10 | 2026-06-25 | SPY | short | pullback | SPY260625P00737000 | 09:40 | 2.18 | 09:42 | 3.21 | profit_target | $+102.59 |
| 11 | 2026-07-02 | SPY | short | pullback | SPY260702P00747000 | 11:05 | 2.16 | 11:07 | 3.18 | profit_target | $+101.63 |
| 12 | 2026-07-06 | SPY | long | pullback | SPY260706C00750000 | 10:54 | 0.89 | 10:57 | 0.80 | volume_faded | $-8.38 |
| 13 | 2026-07-07 | SPY | long | squeeze | SPY260707C00747000 | 11:45 | 0.80 | 11:49 | 0.93 | trailing_stop | $+12.95 |
| 14 | 2026-07-08 | SPY | short | squeeze | SPY260708P00741000 | 11:15 | 1.59 | 11:19 | 1.54 | trailing_stop | $-5.46 |
| 15 | 2026-07-08 | SPY | short | pullback | SPY260708P00741000 | 11:23 | 1.81 | 11:32 | 1.95 | trailing_stop | $+14.08 |
| 16 | 2026-07-09 | SPY | short | pullback | SPY260709P00748000 | 10:53 | 1.64 | 10:54 | 1.29 | trailing_stop | $-35.47 |
| 17 | 2026-07-10 | SPY | short | squeeze | SPY260710P00749000 | 10:33 | 1.30 | 10:33 | 1.02 | trailing_stop | $-27.98 |
| 18 | 2026-07-10 | SPY | short | squeeze | SPY260710P00750000 | 10:34 | 1.31 | 10:34 | 1.02 | trailing_stop | $-28.20 |
| 19 | 2026-07-13 | SPY | short | pullback | SPY260713P00752000 | 10:54 | 1.30 | 10:55 | 1.07 | setup_failed | $-22.72 |
| 20 | 2026-07-16 | SPY | long | pullback | SPY260716C00754000 | 10:45 | 1.35 | 10:48 | 1.19 | volume_faded | $-16.06 |
| 21 | 2026-07-17 | SPY | long | pullback | SPY260717C00745000 | 11:47 | 1.63 | 11:48 | 1.47 | setup_failed | $-16.20 |
| 22 | 2026-07-21 | SPY | long | squeeze | SPY260721C00747000 | 10:19 | 0.83 | 10:21 | 0.68 | trailing_stop | $-14.41 |
| 23 | 2026-07-23 | SPY | short | pullback | SPY260723P00740000 | 10:20 | 2.17 | 10:21 | 1.74 | setup_failed | $-42.82 |
| 24 | 2026-07-23 | SPY | short | pullback | SPY260723P00737000 | 11:23 | 2.12 | 11:32 | 2.29 | trailing_stop | $+16.55 |
| 25 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:11 | 1.75 | 11:11 | 1.81 | trailing_stop | $+5.86 |
| 26 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:12 | 1.91 | 11:15 | 2.80 | profit_target | $+89.65 |
| 27 | 2026-07-28 | SPY | short | pullback | SPY260728P00737000 | 10:15 | 2.02 | 10:21 | 1.61 | setup_failed | $-41.24 |
| 28 | 2026-07-31 | SPY | long | pullback | SPY260731C00742000 | 11:16 | 1.87 | 11:16 | 1.46 | hard_stop | $-40.32 |
| 29 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:17 | 0.97 | 11:20 | 1.10 | volume_faded | $+12.86 |
| 30 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:34 | 1.06 | 11:42 | 1.20 | volume_faded | $+13.48 |
| 31 | 2026-08-05 | SPY | short | squeeze | SPY260805P00772000 | 10:54 | 1.49 | 10:57 | 1.18 | trailing_stop | $-30.54 |
| 32 | 2026-08-05 | SPY | short | squeeze | SPY260805P00771000 | 11:50 | 1.37 | 11:58 | 1.43 | trailing_stop | $+6.79 |
| 33 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 09:58 | 1.31 | 10:05 | 1.50 | volume_faded | $+19.38 |
| 34 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 10:30 | 1.40 | 10:31 | 1.18 | setup_failed | $-22.14 |
| 35 | 2026-08-18 | SPY | long | pullback | SPY260818C00768000 | 10:36 | 1.74 | 10:39 | 1.73 | volume_faded | $-0.96 |
| 36 | 2026-08-20 | SPY | long | pullback | SPY260820C00767000 | 11:01 | 1.29 | 11:03 | 1.51 | trailing_stop | $+22.62 |
| 37 | 2026-08-20 | SPY | short | pullback | SPY260820P00766000 | 11:36 | 1.16 | 11:39 | 1.23 | volume_faded | $+7.20 |
| 38 | 2026-08-21 | SPY | short | pullback | SPY260821P00765000 | 10:20 | 1.29 | 10:22 | 1.01 | trailing_stop | $-27.76 |
| 39 | 2026-08-24 | SPY | long | pullback | SPY260824C00763000 | 10:22 | 1.21 | 10:23 | 1.04 | setup_failed | $-17.50 |
| 40 | 2026-08-25 | SPY | long | pullback | SPY260825C00765000 | 11:29 | 0.92 | 11:32 | 0.82 | setup_failed | $-9.48 |
| 41 | 2026-08-27 | SPY | long | squeeze | SPY260827C00771000 | 10:50 | 0.69 | 10:53 | 0.59 | trailing_stop | $-10.56 |
| 42 | 2026-09-08 | SPY | short | pullback | SPY260908P00768000 | 11:23 | 1.18 | 11:24 | 0.93 | hard_stop | $-25.56 |
| 43 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 10:17 | 1.03 | 10:25 | 1.07 | trailing_stop | $+4.39 |
| 44 | 2026-09-09 | SPY | long | squeeze | SPY260909C00765000 | 11:01 | 0.67 | 11:01 | 0.53 | trailing_stop | $-14.54 |
| 45 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 11:02 | 0.90 | 11:16 | 1.63 | trailing_stop | $+73.31 |
| 46 | 2026-09-10 | SPY | long | pullback | SPY260910C00759000 | 10:58 | 1.44 | 11:01 | 1.13 | hard_stop | $-31.07 |
| 47 | 2026-09-14 | SPY | long | pullback | SPY260914C00760000 | 10:02 | 1.52 | 10:05 | 1.31 | volume_faded | $-20.66 |
| 48 | 2026-09-15 | SPY | long | squeeze | SPY260915C00758000 | 11:43 | 0.81 | 11:46 | 0.64 | trailing_stop | $-17.08 |
| 49 | 2026-09-18 | SPY | short | squeeze | SPY260918P00758000 | 10:44 | 0.77 | 10:46 | 0.61 | trailing_stop | $-15.35 |
| 50 | 2026-09-18 | SPY | long | squeeze | SPY260918C00760000 | 10:51 | 0.88 | 11:02 | 0.82 | trailing_stop | $-5.40 |
| 51 | 2026-09-22 | SPY | short | pullback | SPY260922P00774000 | 10:40 | 1.31 | 10:44 | 1.28 | trailing_stop | $-2.61 |
| 52 | 2026-09-25 | SPY | long | pullback | SPY260925C00769000 | 11:31 | 1.26 | 11:34 | 1.24 | trailing_stop | $-2.53 |
| 53 | 2026-10-01 | SPY | short | pullback | SPY261001P00760000 | 11:44 | 1.64 | 11:47 | 1.29 | trailing_stop | $-35.47 |
| 54 | 2026-10-05 | SPY | short | squeeze | SPY261005P00770000 | 10:01 | 1.19 | 10:01 | 0.94 | trailing_stop | $-25.78 |
| 55 | 2026-10-05 | SPY | long | pullback | SPY261005C00772000 | 11:24 | 1.31 | 11:27 | 1.25 | volume_faded | $-5.12 |
| 56 | 2026-10-12 | SPY | short | pullback | SPY261012P00779000 | 11:24 | 1.26 | 11:30 | 1.14 | volume_faded | $-12.80 |
| 57 | 2026-10-14 | SPY | long | squeeze | SPY261014C00774000 | 10:35 | 0.91 | 10:36 | 0.71 | trailing_stop | $-19.44 |
| 58 | 2026-10-14 | SPY | short | squeeze | SPY261014P00772000 | 10:38 | 1.03 | 10:40 | 0.90 | trailing_stop | $-12.86 |
| 59 | 2026-10-21 | SPY | long | pullback | SPY261021C00770000 | 09:42 | 2.22 | 09:43 | 1.74 | trailing_stop | $-48.03 |
| 60 | 2026-10-22 | SPY | short | pullback | SPY261022P00763000 | 11:15 | 1.90 | 11:16 | 1.71 | setup_failed | $-19.20 |
| 61 | 2026-10-22 | SPY | long | squeeze | SPY261022C00764000 | 11:18 | 1.50 | 11:27 | 1.56 | trailing_stop | $+6.08 |
| 62 | 2026-10-23 | SPY | short | squeeze | SPY261023P00759000 | 10:17 | 1.81 | 10:21 | 1.65 | trailing_stop | $-15.90 |

## spy/v2_no_volume_fade

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 62 | 30.6% | $+32.33 | $-22.30 | $-344.64 | $-5.56 | $+102.59 | $-48.03 | $+102.59 | $-77.33 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 62 | 30.6% | $-344.64 | $-5.56 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 3 | 100.0% | $+293.87 | $+97.96 |
| time_stop | 7 | 71.4% | $+62.18 | $+8.88 |
| hard_stop | 3 | 0.0% | $-96.95 | $-32.32 |
| setup_failed | 11 | 0.0% | $-259.86 | $-23.62 |
| trailing_stop | 38 | 28.9% | $-343.88 | $-9.05 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 31 | 32.3% | $-158.20 | $-5.10 |
| short | 31 | 29.0% | $-186.44 | $-6.01 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-03 | SPY | short | pullback | SPY260603P00757000 | 11:15 | 1.81 | 11:16 | 1.65 | setup_failed | $-15.90 |
| 2 | 2026-06-03 | SPY | short | pullback | SPY260603P00756000 | 11:35 | 1.40 | 11:45 | 1.65 | time_stop | $+24.90 |
| 3 | 2026-06-04 | SPY | long | squeeze | SPY260604C00755000 | 11:01 | 0.87 | 11:20 | 1.28 | trailing_stop | $+41.09 |
| 4 | 2026-06-12 | SPY | short | squeeze | SPY260612P00738000 | 10:44 | 2.78 | 10:50 | 2.54 | trailing_stop | $-24.44 |
| 5 | 2026-06-15 | SPY | long | squeeze | SPY260615C00754000 | 10:49 | 1.11 | 11:34 | 1.51 | trailing_stop | $+40.13 |
| 6 | 2026-06-22 | SPY | short | pullback | SPY260622P00745000 | 11:20 | 1.93 | 11:23 | 1.51 | trailing_stop | $-41.64 |
| 7 | 2026-06-23 | SPY | short | pullback | SPY260623P00735000 | 11:39 | 1.94 | 11:43 | 1.58 | setup_failed | $-36.02 |
| 8 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:18 | 1.70 | 11:24 | 1.34 | trailing_stop | $-36.79 |
| 9 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:30 | 1.88 | 11:33 | 1.47 | trailing_stop | $-40.54 |
| 10 | 2026-06-25 | SPY | short | pullback | SPY260625P00737000 | 09:40 | 2.18 | 09:42 | 3.21 | profit_target | $+102.59 |
| 11 | 2026-07-02 | SPY | short | pullback | SPY260702P00747000 | 11:05 | 2.16 | 11:07 | 3.18 | profit_target | $+101.63 |
| 12 | 2026-07-06 | SPY | long | pullback | SPY260706C00750000 | 10:54 | 0.89 | 11:04 | 0.88 | time_stop | $-0.54 |
| 13 | 2026-07-07 | SPY | long | squeeze | SPY260707C00747000 | 11:45 | 0.80 | 11:49 | 0.93 | trailing_stop | $+12.95 |
| 14 | 2026-07-08 | SPY | short | squeeze | SPY260708P00741000 | 11:15 | 1.59 | 11:19 | 1.54 | trailing_stop | $-5.46 |
| 15 | 2026-07-08 | SPY | short | pullback | SPY260708P00741000 | 11:23 | 1.81 | 11:32 | 1.95 | trailing_stop | $+14.08 |
| 16 | 2026-07-09 | SPY | short | pullback | SPY260709P00748000 | 10:53 | 1.64 | 10:54 | 1.29 | trailing_stop | $-35.47 |
| 17 | 2026-07-10 | SPY | short | squeeze | SPY260710P00749000 | 10:33 | 1.30 | 10:33 | 1.02 | trailing_stop | $-27.98 |
| 18 | 2026-07-10 | SPY | short | squeeze | SPY260710P00750000 | 10:34 | 1.31 | 10:34 | 1.02 | trailing_stop | $-28.20 |
| 19 | 2026-07-13 | SPY | short | pullback | SPY260713P00752000 | 10:54 | 1.30 | 10:55 | 1.07 | setup_failed | $-22.72 |
| 20 | 2026-07-16 | SPY | long | pullback | SPY260716C00754000 | 10:45 | 1.35 | 10:50 | 1.06 | trailing_stop | $-29.08 |
| 21 | 2026-07-17 | SPY | long | pullback | SPY260717C00745000 | 11:47 | 1.63 | 11:48 | 1.47 | setup_failed | $-16.20 |
| 22 | 2026-07-21 | SPY | long | squeeze | SPY260721C00747000 | 10:19 | 0.83 | 10:21 | 0.68 | trailing_stop | $-14.41 |
| 23 | 2026-07-23 | SPY | short | pullback | SPY260723P00740000 | 10:20 | 2.17 | 10:21 | 1.74 | setup_failed | $-42.82 |
| 24 | 2026-07-23 | SPY | short | pullback | SPY260723P00737000 | 11:23 | 2.12 | 11:32 | 2.29 | trailing_stop | $+16.55 |
| 25 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:11 | 1.75 | 11:11 | 1.81 | trailing_stop | $+5.86 |
| 26 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:12 | 1.91 | 11:15 | 2.80 | profit_target | $+89.65 |
| 27 | 2026-07-28 | SPY | short | pullback | SPY260728P00737000 | 10:15 | 2.02 | 10:21 | 1.61 | setup_failed | $-41.24 |
| 28 | 2026-07-31 | SPY | long | pullback | SPY260731C00742000 | 11:16 | 1.87 | 11:16 | 1.46 | hard_stop | $-40.32 |
| 29 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:17 | 0.97 | 11:26 | 0.95 | trailing_stop | $-1.94 |
| 30 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:34 | 1.06 | 11:44 | 1.16 | time_stop | $+9.56 |
| 31 | 2026-08-05 | SPY | short | squeeze | SPY260805P00772000 | 10:54 | 1.49 | 10:57 | 1.18 | trailing_stop | $-30.54 |
| 32 | 2026-08-05 | SPY | short | squeeze | SPY260805P00771000 | 11:50 | 1.37 | 11:58 | 1.43 | trailing_stop | $+6.79 |
| 33 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 09:58 | 1.31 | 10:08 | 1.39 | time_stop | $+8.60 |
| 34 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 10:30 | 1.40 | 10:31 | 1.18 | setup_failed | $-22.14 |
| 35 | 2026-08-18 | SPY | long | pullback | SPY260818C00768000 | 10:36 | 1.74 | 10:41 | 1.58 | setup_failed | $-16.64 |
| 36 | 2026-08-20 | SPY | long | pullback | SPY260820C00767000 | 11:01 | 1.29 | 11:03 | 1.51 | trailing_stop | $+22.62 |
| 37 | 2026-08-20 | SPY | short | pullback | SPY260820P00766000 | 11:36 | 1.16 | 11:46 | 1.32 | time_stop | $+16.02 |
| 38 | 2026-08-21 | SPY | short | pullback | SPY260821P00765000 | 10:20 | 1.29 | 10:22 | 1.01 | trailing_stop | $-27.76 |
| 39 | 2026-08-24 | SPY | long | pullback | SPY260824C00763000 | 10:22 | 1.21 | 10:23 | 1.04 | setup_failed | $-17.50 |
| 40 | 2026-08-25 | SPY | long | pullback | SPY260825C00765000 | 11:29 | 0.92 | 11:32 | 0.82 | setup_failed | $-9.48 |
| 41 | 2026-08-27 | SPY | long | squeeze | SPY260827C00771000 | 10:50 | 0.69 | 10:53 | 0.59 | trailing_stop | $-10.56 |
| 42 | 2026-09-08 | SPY | short | pullback | SPY260908P00768000 | 11:23 | 1.18 | 11:24 | 0.93 | hard_stop | $-25.56 |
| 43 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 10:17 | 1.03 | 10:25 | 1.07 | trailing_stop | $+4.39 |
| 44 | 2026-09-09 | SPY | long | squeeze | SPY260909C00765000 | 11:01 | 0.67 | 11:01 | 0.53 | trailing_stop | $-14.54 |
| 45 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 11:02 | 0.90 | 11:16 | 1.63 | trailing_stop | $+73.31 |
| 46 | 2026-09-10 | SPY | long | pullback | SPY260910C00759000 | 10:58 | 1.44 | 11:01 | 1.13 | hard_stop | $-31.07 |
| 47 | 2026-09-14 | SPY | long | pullback | SPY260914C00760000 | 10:02 | 1.52 | 10:12 | 1.34 | trailing_stop | $-17.93 |
| 48 | 2026-09-15 | SPY | long | squeeze | SPY260915C00758000 | 11:43 | 0.81 | 11:46 | 0.64 | trailing_stop | $-17.08 |
| 49 | 2026-09-18 | SPY | short | squeeze | SPY260918P00758000 | 10:44 | 0.77 | 10:46 | 0.61 | trailing_stop | $-15.35 |
| 50 | 2026-09-18 | SPY | long | squeeze | SPY260918C00760000 | 10:51 | 0.88 | 11:02 | 0.82 | trailing_stop | $-5.40 |
| 51 | 2026-09-22 | SPY | short | pullback | SPY260922P00774000 | 10:40 | 1.31 | 10:44 | 1.28 | trailing_stop | $-2.61 |
| 52 | 2026-09-25 | SPY | long | pullback | SPY260925C00769000 | 11:31 | 1.26 | 11:34 | 1.24 | trailing_stop | $-2.53 |
| 53 | 2026-10-01 | SPY | short | pullback | SPY261001P00760000 | 11:44 | 1.64 | 11:47 | 1.29 | trailing_stop | $-35.47 |
| 54 | 2026-10-05 | SPY | short | squeeze | SPY261005P00770000 | 10:01 | 1.19 | 10:01 | 0.94 | trailing_stop | $-25.78 |
| 55 | 2026-10-05 | SPY | long | pullback | SPY261005C00772000 | 11:24 | 1.31 | 11:34 | 1.48 | time_stop | $+17.42 |
| 56 | 2026-10-12 | SPY | short | pullback | SPY261012P00779000 | 11:24 | 1.26 | 11:34 | 1.13 | time_stop | $-13.78 |
| 57 | 2026-10-14 | SPY | long | squeeze | SPY261014C00774000 | 10:35 | 0.91 | 10:36 | 0.71 | trailing_stop | $-19.44 |
| 58 | 2026-10-14 | SPY | short | squeeze | SPY261014P00772000 | 10:38 | 1.03 | 10:40 | 0.90 | trailing_stop | $-12.86 |
| 59 | 2026-10-21 | SPY | long | pullback | SPY261021C00770000 | 09:42 | 2.22 | 09:43 | 1.74 | trailing_stop | $-48.03 |
| 60 | 2026-10-22 | SPY | short | pullback | SPY261022P00763000 | 11:15 | 1.90 | 11:16 | 1.71 | setup_failed | $-19.20 |
| 61 | 2026-10-22 | SPY | long | squeeze | SPY261022C00764000 | 11:18 | 1.50 | 11:27 | 1.56 | trailing_stop | $+6.08 |
| 62 | 2026-10-23 | SPY | short | squeeze | SPY261023P00759000 | 10:17 | 1.81 | 10:21 | 1.65 | trailing_stop | $-15.90 |

## spy/v3_wider_stops

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 64 | 23.4% | $+42.67 | $-21.87 | $-431.59 | $-6.74 | $+136.76 | $-63.60 | $+136.76 | $-81.68 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 64 | 23.4% | $-431.59 | $-6.74 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 2 | 100.0% | $+204.22 | $+102.11 |
| noon_shutdown | 3 | 100.0% | $+199.82 | $+66.61 |
| hard_stop | 1 | 0.0% | $-37.15 | $-37.15 |
| volume_faded | 26 | 23.1% | $-113.84 | $-4.38 |
| setup_failed | 11 | 0.0% | $-307.02 | $-27.91 |
| trailing_stop | 21 | 19.0% | $-377.62 | $-17.98 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 32 | 28.1% | $-142.50 | $-4.45 |
| short | 32 | 18.8% | $-289.09 | $-9.03 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-03 | SPY | short | pullback | SPY260603P00757000 | 11:15 | 1.81 | 11:16 | 1.65 | setup_failed | $-15.90 |
| 2 | 2026-06-03 | SPY | short | pullback | SPY260603P00756000 | 11:35 | 1.40 | 11:36 | 1.31 | volume_faded | $-8.42 |
| 3 | 2026-06-04 | SPY | long | squeeze | SPY260604C00755000 | 11:01 | 0.87 | 11:43 | 1.12 | trailing_stop | $+25.12 |
| 4 | 2026-06-12 | SPY | short | squeeze | SPY260612P00738000 | 10:44 | 2.78 | 10:52 | 2.22 | trailing_stop | $-56.20 |
| 5 | 2026-06-15 | SPY | long | squeeze | SPY260615C00754000 | 10:49 | 1.11 | 12:00 | 2.48 | noon_shutdown | $+136.76 |
| 6 | 2026-06-22 | SPY | short | pullback | SPY260622P00745000 | 11:20 | 1.93 | 11:22 | 1.77 | volume_faded | $-15.40 |
| 7 | 2026-06-23 | SPY | short | pullback | SPY260623P00735000 | 11:39 | 1.94 | 11:40 | 1.88 | volume_faded | $-5.64 |
| 8 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:18 | 1.70 | 11:19 | 1.59 | volume_faded | $-11.58 |
| 9 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:30 | 1.88 | 11:31 | 1.58 | volume_faded | $-29.90 |
| 10 | 2026-06-25 | SPY | short | pullback | SPY260625P00737000 | 09:40 | 2.18 | 09:42 | 3.21 | profit_target | $+102.59 |
| 11 | 2026-07-02 | SPY | short | pullback | SPY260702P00747000 | 11:05 | 2.16 | 11:07 | 3.18 | profit_target | $+101.63 |
| 12 | 2026-07-06 | SPY | long | pullback | SPY260706C00750000 | 10:54 | 0.89 | 10:55 | 0.78 | volume_faded | $-10.34 |
| 13 | 2026-07-07 | SPY | long | squeeze | SPY260707C00747000 | 11:45 | 0.80 | 12:00 | 1.19 | noon_shutdown | $+39.02 |
| 14 | 2026-07-08 | SPY | short | squeeze | SPY260708P00741000 | 11:15 | 1.59 | 11:19 | 1.34 | trailing_stop | $-24.66 |
| 15 | 2026-07-08 | SPY | short | pullback | SPY260708P00741000 | 11:23 | 1.81 | 11:28 | 2.19 | volume_faded | $+38.00 |
| 16 | 2026-07-09 | SPY | short | pullback | SPY260709P00748000 | 10:53 | 1.64 | 10:54 | 1.31 | setup_failed | $-32.90 |
| 17 | 2026-07-10 | SPY | short | squeeze | SPY260710P00749000 | 10:33 | 1.30 | 10:33 | 0.89 | trailing_stop | $-40.68 |
| 18 | 2026-07-10 | SPY | short | squeeze | SPY260710P00750000 | 10:34 | 1.31 | 10:34 | 0.90 | trailing_stop | $-41.00 |
| 19 | 2026-07-13 | SPY | short | pullback | SPY260713P00752000 | 10:54 | 1.30 | 10:55 | 1.07 | setup_failed | $-22.72 |
| 20 | 2026-07-16 | SPY | long | pullback | SPY260716C00754000 | 10:45 | 1.35 | 10:46 | 1.26 | volume_faded | $-8.22 |
| 21 | 2026-07-17 | SPY | long | pullback | SPY260717C00745000 | 11:47 | 1.63 | 11:48 | 1.47 | setup_failed | $-16.20 |
| 22 | 2026-07-21 | SPY | long | squeeze | SPY260721C00747000 | 10:19 | 0.83 | 10:38 | 0.88 | trailing_stop | $+5.19 |
| 23 | 2026-07-23 | SPY | short | pullback | SPY260723P00740000 | 10:20 | 2.17 | 10:21 | 1.74 | setup_failed | $-42.82 |
| 24 | 2026-07-23 | SPY | short | pullback | SPY260723P00737000 | 11:23 | 2.12 | 11:24 | 1.78 | volume_faded | $-33.80 |
| 25 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:11 | 1.75 | 11:11 | 1.81 | trailing_stop | $+5.86 |
| 26 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:12 | 1.91 | 11:13 | 1.74 | volume_faded | $-16.30 |
| 27 | 2026-07-28 | SPY | short | pullback | SPY260728P00737000 | 10:15 | 2.02 | 10:16 | 1.96 | volume_faded | $-5.96 |
| 28 | 2026-07-31 | SPY | long | pullback | SPY260731C00742000 | 11:16 | 1.87 | 11:17 | 1.42 | setup_failed | $-44.56 |
| 29 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:17 | 0.97 | 11:18 | 0.95 | volume_faded | $-1.84 |
| 30 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:34 | 1.06 | 11:35 | 1.00 | volume_faded | $-6.12 |
| 31 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:38 | 1.04 | 11:40 | 1.19 | volume_faded | $+14.54 |
| 32 | 2026-08-05 | SPY | short | squeeze | SPY260805P00772000 | 10:54 | 1.49 | 11:00 | 1.04 | trailing_stop | $-45.33 |
| 33 | 2026-08-05 | SPY | short | squeeze | SPY260805P00771000 | 11:50 | 1.37 | 12:00 | 1.61 | noon_shutdown | $+24.04 |
| 34 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 09:58 | 1.31 | 09:59 | 1.37 | volume_faded | $+6.64 |
| 35 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 10:30 | 1.40 | 10:31 | 1.18 | setup_failed | $-22.14 |
| 36 | 2026-08-18 | SPY | long | pullback | SPY260818C00768000 | 10:36 | 1.74 | 10:37 | 1.66 | volume_faded | $-8.80 |
| 37 | 2026-08-20 | SPY | long | pullback | SPY260820C00767000 | 11:01 | 1.29 | 11:04 | 1.63 | volume_faded | $+34.16 |
| 38 | 2026-08-20 | SPY | short | pullback | SPY260820P00766000 | 11:36 | 1.16 | 11:37 | 1.03 | volume_faded | $-13.38 |
| 39 | 2026-08-21 | SPY | short | pullback | SPY260821P00765000 | 10:20 | 1.29 | 10:21 | 1.19 | volume_faded | $-9.94 |
| 40 | 2026-08-24 | SPY | long | pullback | SPY260824C00763000 | 10:22 | 1.21 | 10:23 | 1.04 | setup_failed | $-17.50 |
| 41 | 2026-08-25 | SPY | long | pullback | SPY260825C00765000 | 11:29 | 0.92 | 11:32 | 0.82 | setup_failed | $-9.48 |
| 42 | 2026-08-27 | SPY | long | squeeze | SPY260827C00771000 | 10:50 | 0.69 | 10:55 | 0.51 | trailing_stop | $-17.91 |
| 43 | 2026-09-08 | SPY | short | pullback | SPY260908P00768000 | 11:23 | 1.18 | 11:24 | 0.81 | hard_stop | $-37.15 |
| 44 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 10:17 | 1.03 | 10:26 | 0.95 | trailing_stop | $-7.67 |
| 45 | 2026-09-09 | SPY | long | squeeze | SPY260909C00765000 | 11:01 | 0.67 | 11:01 | 0.46 | trailing_stop | $-21.14 |
| 46 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 11:02 | 0.90 | 11:30 | 1.63 | trailing_stop | $+73.51 |
| 47 | 2026-09-10 | SPY | long | pullback | SPY260910C00759000 | 10:58 | 1.44 | 10:59 | 1.34 | volume_faded | $-9.56 |
| 48 | 2026-09-14 | SPY | long | pullback | SPY260914C00760000 | 10:02 | 1.52 | 10:03 | 1.27 | volume_faded | $-24.58 |
| 49 | 2026-09-15 | SPY | long | squeeze | SPY260915C00758000 | 11:43 | 0.81 | 11:49 | 0.56 | trailing_stop | $-25.01 |
| 50 | 2026-09-18 | SPY | short | squeeze | SPY260918P00758000 | 10:44 | 0.77 | 10:49 | 0.54 | trailing_stop | $-22.99 |
| 51 | 2026-09-18 | SPY | long | squeeze | SPY260918C00760000 | 10:51 | 0.88 | 11:16 | 0.72 | trailing_stop | $-15.69 |
| 52 | 2026-09-22 | SPY | short | pullback | SPY260922P00774000 | 10:40 | 1.31 | 10:42 | 1.51 | volume_faded | $+20.36 |
| 53 | 2026-09-22 | SPY | short | squeeze | SPY260922P00773000 | 10:43 | 1.03 | 10:49 | 0.71 | trailing_stop | $-32.35 |
| 54 | 2026-09-25 | SPY | long | pullback | SPY260925C00769000 | 11:31 | 1.26 | 11:33 | 1.39 | volume_faded | $+12.68 |
| 55 | 2026-10-01 | SPY | short | pullback | SPY261001P00760000 | 11:44 | 1.64 | 11:45 | 1.49 | volume_faded | $-15.26 |
| 56 | 2026-10-05 | SPY | short | squeeze | SPY261005P00770000 | 10:01 | 1.19 | 10:02 | 0.82 | trailing_stop | $-37.02 |
| 57 | 2026-10-05 | SPY | long | pullback | SPY261005C00772000 | 11:24 | 1.31 | 11:25 | 1.30 | volume_faded | $-0.22 |
| 58 | 2026-10-12 | SPY | short | pullback | SPY261012P00779000 | 11:24 | 1.26 | 11:25 | 1.22 | volume_faded | $-4.96 |
| 59 | 2026-10-14 | SPY | long | squeeze | SPY261014C00774000 | 10:35 | 0.91 | 10:37 | 0.62 | trailing_stop | $-28.35 |
| 60 | 2026-10-14 | SPY | short | squeeze | SPY261014P00772000 | 10:38 | 1.03 | 10:43 | 0.79 | trailing_stop | $-24.13 |
| 61 | 2026-10-21 | SPY | long | pullback | SPY261021C00770000 | 09:42 | 2.22 | 09:43 | 1.59 | setup_failed | $-63.60 |
| 62 | 2026-10-22 | SPY | short | pullback | SPY261022P00763000 | 11:15 | 1.90 | 11:16 | 1.71 | setup_failed | $-19.20 |
| 63 | 2026-10-22 | SPY | long | squeeze | SPY261022C00764000 | 11:18 | 1.50 | 11:29 | 1.37 | trailing_stop | $-13.43 |
| 64 | 2026-10-23 | SPY | short | squeeze | SPY261023P00759000 | 10:17 | 1.81 | 10:30 | 1.47 | trailing_stop | $-33.74 |

## spy/v4_no_bar_exits

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 62 | 35.5% | $+32.13 | $-24.86 | $-287.54 | $-4.64 | $+102.59 | $-48.03 | $+102.59 | $-77.33 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 62 | 35.5% | $-287.54 | $-4.64 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 3 | 100.0% | $+293.87 | $+97.96 |
| time_stop | 9 | 77.8% | $+148.66 | $+16.52 |
| hard_stop | 4 | 0.0% | $-127.13 | $-31.78 |
| trailing_stop | 46 | 26.1% | $-602.94 | $-13.11 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 31 | 38.7% | $-108.77 | $-3.51 |
| short | 31 | 32.3% | $-178.77 | $-5.77 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-03 | SPY | short | pullback | SPY260603P00757000 | 11:15 | 1.81 | 11:25 | 2.12 | time_stop | $+31.14 |
| 2 | 2026-06-03 | SPY | short | pullback | SPY260603P00756000 | 11:35 | 1.40 | 11:45 | 1.65 | time_stop | $+24.90 |
| 3 | 2026-06-04 | SPY | long | squeeze | SPY260604C00755000 | 11:01 | 0.87 | 11:20 | 1.28 | trailing_stop | $+41.09 |
| 4 | 2026-06-12 | SPY | short | squeeze | SPY260612P00738000 | 10:44 | 2.78 | 10:50 | 2.54 | trailing_stop | $-24.44 |
| 5 | 2026-06-15 | SPY | long | squeeze | SPY260615C00754000 | 10:49 | 1.11 | 11:34 | 1.51 | trailing_stop | $+40.13 |
| 6 | 2026-06-22 | SPY | short | pullback | SPY260622P00745000 | 11:20 | 1.93 | 11:23 | 1.51 | trailing_stop | $-41.64 |
| 7 | 2026-06-23 | SPY | short | pullback | SPY260623P00735000 | 11:39 | 1.94 | 11:44 | 1.52 | trailing_stop | $-41.86 |
| 8 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:18 | 1.70 | 11:24 | 1.34 | trailing_stop | $-36.79 |
| 9 | 2026-06-24 | SPY | long | pullback | SPY260624C00739000 | 11:30 | 1.88 | 11:33 | 1.47 | trailing_stop | $-40.54 |
| 10 | 2026-06-25 | SPY | short | pullback | SPY260625P00737000 | 09:40 | 2.18 | 09:42 | 3.21 | profit_target | $+102.59 |
| 11 | 2026-07-02 | SPY | short | pullback | SPY260702P00747000 | 11:05 | 2.16 | 11:07 | 3.18 | profit_target | $+101.63 |
| 12 | 2026-07-06 | SPY | long | pullback | SPY260706C00750000 | 10:54 | 0.89 | 11:04 | 0.88 | time_stop | $-0.54 |
| 13 | 2026-07-07 | SPY | long | squeeze | SPY260707C00747000 | 11:45 | 0.80 | 11:49 | 0.93 | trailing_stop | $+12.95 |
| 14 | 2026-07-08 | SPY | short | squeeze | SPY260708P00741000 | 11:15 | 1.59 | 11:19 | 1.54 | trailing_stop | $-5.46 |
| 15 | 2026-07-08 | SPY | short | pullback | SPY260708P00741000 | 11:23 | 1.81 | 11:32 | 1.95 | trailing_stop | $+14.08 |
| 16 | 2026-07-09 | SPY | short | pullback | SPY260709P00748000 | 10:53 | 1.64 | 10:54 | 1.29 | trailing_stop | $-35.47 |
| 17 | 2026-07-10 | SPY | short | squeeze | SPY260710P00749000 | 10:33 | 1.30 | 10:33 | 1.02 | trailing_stop | $-27.98 |
| 18 | 2026-07-10 | SPY | short | squeeze | SPY260710P00750000 | 10:34 | 1.31 | 10:34 | 1.02 | trailing_stop | $-28.20 |
| 19 | 2026-07-13 | SPY | short | pullback | SPY260713P00752000 | 10:54 | 1.30 | 10:56 | 1.02 | trailing_stop | $-27.98 |
| 20 | 2026-07-16 | SPY | long | pullback | SPY260716C00754000 | 10:45 | 1.35 | 10:50 | 1.06 | trailing_stop | $-29.08 |
| 21 | 2026-07-17 | SPY | long | pullback | SPY260717C00745000 | 11:47 | 1.63 | 11:57 | 2.19 | time_stop | $+55.34 |
| 22 | 2026-07-21 | SPY | long | squeeze | SPY260721C00747000 | 10:19 | 0.83 | 10:21 | 0.68 | trailing_stop | $-14.41 |
| 23 | 2026-07-23 | SPY | short | pullback | SPY260723P00740000 | 10:20 | 2.17 | 10:22 | 1.70 | trailing_stop | $-46.93 |
| 24 | 2026-07-23 | SPY | short | pullback | SPY260723P00737000 | 11:23 | 2.12 | 11:32 | 2.29 | trailing_stop | $+16.55 |
| 25 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:11 | 1.75 | 11:11 | 1.81 | trailing_stop | $+5.86 |
| 26 | 2026-07-24 | SPY | long | pullback | SPY260724C00740000 | 11:12 | 1.91 | 11:15 | 2.80 | profit_target | $+89.65 |
| 27 | 2026-07-28 | SPY | short | pullback | SPY260728P00737000 | 10:15 | 2.02 | 10:22 | 1.58 | trailing_stop | $-43.62 |
| 28 | 2026-07-31 | SPY | long | pullback | SPY260731C00742000 | 11:16 | 1.87 | 11:16 | 1.46 | hard_stop | $-40.32 |
| 29 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:17 | 0.97 | 11:26 | 0.95 | trailing_stop | $-1.94 |
| 30 | 2026-08-03 | SPY | long | pullback | SPY260803C00755000 | 11:34 | 1.06 | 11:44 | 1.16 | time_stop | $+9.56 |
| 31 | 2026-08-05 | SPY | short | squeeze | SPY260805P00772000 | 10:54 | 1.49 | 10:57 | 1.18 | trailing_stop | $-30.54 |
| 32 | 2026-08-05 | SPY | short | squeeze | SPY260805P00771000 | 11:50 | 1.37 | 11:58 | 1.43 | trailing_stop | $+6.79 |
| 33 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 09:58 | 1.31 | 10:08 | 1.39 | time_stop | $+8.60 |
| 34 | 2026-08-11 | SPY | long | pullback | SPY260811C00773000 | 10:30 | 1.40 | 10:38 | 1.10 | hard_stop | $-30.18 |
| 35 | 2026-08-18 | SPY | long | pullback | SPY260818C00768000 | 10:36 | 1.74 | 10:43 | 1.37 | trailing_stop | $-37.67 |
| 36 | 2026-08-20 | SPY | long | pullback | SPY260820C00767000 | 11:01 | 1.29 | 11:03 | 1.51 | trailing_stop | $+22.62 |
| 37 | 2026-08-20 | SPY | short | pullback | SPY260820P00766000 | 11:36 | 1.16 | 11:46 | 1.32 | time_stop | $+16.02 |
| 38 | 2026-08-21 | SPY | short | pullback | SPY260821P00765000 | 10:20 | 1.29 | 10:22 | 1.01 | trailing_stop | $-27.76 |
| 39 | 2026-08-24 | SPY | long | pullback | SPY260824C00763000 | 10:22 | 1.21 | 10:24 | 0.95 | trailing_stop | $-26.22 |
| 40 | 2026-08-25 | SPY | long | pullback | SPY260825C00765000 | 11:29 | 0.92 | 11:34 | 0.98 | trailing_stop | $+6.20 |
| 41 | 2026-08-27 | SPY | long | squeeze | SPY260827C00771000 | 10:50 | 0.69 | 10:53 | 0.59 | trailing_stop | $-10.56 |
| 42 | 2026-09-08 | SPY | short | pullback | SPY260908P00768000 | 11:23 | 1.18 | 11:24 | 0.93 | hard_stop | $-25.56 |
| 43 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 10:17 | 1.03 | 10:25 | 1.07 | trailing_stop | $+4.39 |
| 44 | 2026-09-09 | SPY | long | squeeze | SPY260909C00765000 | 11:01 | 0.67 | 11:01 | 0.53 | trailing_stop | $-14.54 |
| 45 | 2026-09-09 | SPY | short | squeeze | SPY260909P00763000 | 11:02 | 0.90 | 11:16 | 1.63 | trailing_stop | $+73.31 |
| 46 | 2026-09-10 | SPY | long | pullback | SPY260910C00759000 | 10:58 | 1.44 | 11:01 | 1.13 | hard_stop | $-31.07 |
| 47 | 2026-09-14 | SPY | long | pullback | SPY260914C00760000 | 10:02 | 1.52 | 10:12 | 1.34 | trailing_stop | $-17.93 |
| 48 | 2026-09-15 | SPY | long | squeeze | SPY260915C00758000 | 11:43 | 0.81 | 11:46 | 0.64 | trailing_stop | $-17.08 |
| 49 | 2026-09-18 | SPY | short | squeeze | SPY260918P00758000 | 10:44 | 0.77 | 10:46 | 0.61 | trailing_stop | $-15.35 |
| 50 | 2026-09-18 | SPY | long | squeeze | SPY260918C00760000 | 10:51 | 0.88 | 11:02 | 0.82 | trailing_stop | $-5.40 |
| 51 | 2026-09-22 | SPY | short | pullback | SPY260922P00774000 | 10:40 | 1.31 | 10:44 | 1.28 | trailing_stop | $-2.61 |
| 52 | 2026-09-25 | SPY | long | pullback | SPY260925C00769000 | 11:31 | 1.26 | 11:34 | 1.24 | trailing_stop | $-2.53 |
| 53 | 2026-10-01 | SPY | short | pullback | SPY261001P00760000 | 11:44 | 1.64 | 11:47 | 1.29 | trailing_stop | $-35.47 |
| 54 | 2026-10-05 | SPY | short | squeeze | SPY261005P00770000 | 10:01 | 1.19 | 10:01 | 0.94 | trailing_stop | $-25.78 |
| 55 | 2026-10-05 | SPY | long | pullback | SPY261005C00772000 | 11:24 | 1.31 | 11:34 | 1.48 | time_stop | $+17.42 |
| 56 | 2026-10-12 | SPY | short | pullback | SPY261012P00779000 | 11:24 | 1.26 | 11:34 | 1.13 | time_stop | $-13.78 |
| 57 | 2026-10-14 | SPY | long | squeeze | SPY261014C00774000 | 10:35 | 0.91 | 10:36 | 0.71 | trailing_stop | $-19.44 |
| 58 | 2026-10-14 | SPY | short | squeeze | SPY261014P00772000 | 10:38 | 1.03 | 10:40 | 0.90 | trailing_stop | $-12.86 |
| 59 | 2026-10-21 | SPY | long | pullback | SPY261021C00770000 | 09:42 | 2.22 | 09:43 | 1.74 | trailing_stop | $-48.03 |
| 60 | 2026-10-22 | SPY | short | pullback | SPY261022P00763000 | 11:15 | 1.90 | 11:17 | 1.49 | trailing_stop | $-40.98 |
| 61 | 2026-10-22 | SPY | long | squeeze | SPY261022C00764000 | 11:18 | 1.50 | 11:27 | 1.56 | trailing_stop | $+6.08 |
| 62 | 2026-10-23 | SPY | short | squeeze | SPY261023P00759000 | 10:17 | 1.81 | 10:21 | 1.65 | trailing_stop | $-15.90 |
