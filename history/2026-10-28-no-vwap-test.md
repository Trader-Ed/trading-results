# No-VWAP test (nv_a, nv_b), October 28

## Findings

- **The gate is not passed.** Without VWAP, the pullback signals still don't move the stock our way more often, or further, than random entries do. That holds for the ATR pick and for SPY, before and after 10:00.
- **nv_a (no VWAP, no chop filter)** about doubles the pullback signals (ATR pick: 130 vs 64; SPY: 163 vs 73). Their in-favour shares (47–53%) sit inside the noise band around 50%, the same as the default and the control.
  - The 25 ATR-pick pullbacks before 10:00 did worse: on average −0.17% at +10 minutes and −0.23% at +30. The random entries before 10:00 averaged +0.18% and +0.11%. With 25 signals that is still close to noise, but it points the wrong way.
- **nv_b (no VWAP, chop filter on EMA 20)** removes most pullback signals (ATR pick: 34; SPY: 42).
  - The ones left on the ATR pick did worse than random: 26% in favour at +10 minutes and an average of −0.15%. That is about 2.7 standard errors below a coin flip.
  - This table holds dozens of comparisons, so one result this far out could be chance. It is not evidence of an edge either way, and certainly not a pass.
- **Squeeze signals** are unchanged in both variants, because the squeeze rule doesn't use VWAP. They stay within noise, as on October 27.
- **Options backtest (for information only):** both variants lose less than the default (nv_a −$285, nv_b −$243, default −$393). Every run's best trade is the same QQQ squeeze trade on 2026-09-03 (+$346). Without it, all three lose between −$589 and −$739.
  - nv_a's extra trades before 10:00 lost $264 over 14 trades.

Partner test, October 28: what happens without VWAP. The default rulebook.yaml is unchanged (squeeze only before 10:00, VWAP warm-up to 10:00, chop filter on VWAP crossings).

Both variants turn VWAP off completely (`indicators.use_vwap: false`): regular step 1 is skipped (doesn't block), VWAP is not a pullback or bounce level, the "held" test and the setup-failed exit use EMA 20 only. All rules can enter from 9:35 (regular rules no longer wait until 10:00).

- **nv_a**: chop filter off.
- **nv_b**: chop filter on EMA 20: 3 or more crossings of EMA 20 in 15 minutes blocks the regular rules.

## Signal test (the gate), 2026-01-02 to 2026-10-23

Same method as the October 27 signal test: every signal inside the entry window (9:35 to 11:50), repeats of the same setup and side within 5 minutes skipped; the stock's move in the signal's direction at +5, +10 and +30 minutes, best and worst within 10 minutes; a random control group of the same size on the same days and names with a random direction (seed 7, so each run has its own control draw). Before / from 10:00 is by the minute the signal bar closes. The October 27 default rows are the October 27 results, re-split by time.

Squeeze rows are identical in all three runs (the squeeze rule doesn't use VWAP or the chop filter), so they are shown once. **Noise** is two standard errors of the in-favour share (100/√count points): a share within 50% ± that is indistinguishable from a coin flip.

### ATR pick

| Group | Run | Count | Avg 5m | Avg 10m | Avg 30m | Best 10m | Worst 10m | In favour 5m | 10m | 30m | Noise (±) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze (all) | all three runs | 69 | -0.011% | -0.001% | +0.066% | +0.235% | -0.239% | 54% | 51% | 55% | 12 pts |
| squeeze long | all three runs | 39 | +0.004% | +0.029% | +0.117% | +0.250% | -0.225% | 59% | 54% | 54% | 16 pts |
| squeeze short | all three runs | 30 | -0.031% | -0.041% | -0.002% | +0.214% | -0.257% | 47% | 47% | 57% | 18 pts |
| pullback (all) | Default (Oct 27) | 64 | -0.010% | -0.005% | -0.008% | +0.213% | -0.222% | 50% | 48% | 52% | 12 pts |
| pullback (all) | nv_a | 130 | +0.013% | -0.022% | -0.031% | +0.233% | -0.240% | 52% | 47% | 53% | 9 pts |
| pullback (all) | nv_b | 34 | -0.022% | -0.145% | -0.229% | +0.198% | -0.341% | 35% | 26% | 38% | 17 pts |
| pullback long | Default (Oct 27) | 36 | -0.013% | -0.018% | -0.008% | +0.192% | -0.210% | 47% | 47% | 50% | 17 pts |
| pullback long | nv_a | 65 | -0.010% | -0.037% | -0.074% | +0.225% | -0.263% | 48% | 46% | 46% | 12 pts |
| pullback long | nv_b | 16 | -0.008% | -0.107% | -0.293% | +0.177% | -0.280% | 31% | 25% | 25% | 25 pts |
| pullback short | Default (Oct 27) | 28 | -0.005% | +0.013% | -0.007% | +0.239% | -0.239% | 54% | 50% | 54% | 19 pts |
| pullback short | nv_a | 65 | +0.036% | -0.007% | +0.013% | +0.240% | -0.218% | 57% | 48% | 60% | 12 pts |
| pullback short | nv_b | 18 | -0.035% | -0.179% | -0.172% | +0.216% | -0.395% | 39% | 28% | 50% | 24 pts |
| pullback before 10:00 | Default (Oct 27) | 0 | - | - | - | - | - | - | - | - | - |
| pullback before 10:00 | nv_a | 25 | +0.027% | -0.166% | -0.228% | +0.371% | -0.456% | 56% | 44% | 48% | 20 pts |
| pullback before 10:00 | nv_b | 7 | +0.024% | -0.368% | -0.733% | +0.253% | -0.588% | 43% | 29% | 29% | 38 pts |
| pullback from 10:00 | Default (Oct 27) | 64 | -0.010% | -0.005% | -0.008% | +0.213% | -0.222% | 50% | 48% | 52% | 12 pts |
| pullback from 10:00 | nv_a | 105 | +0.010% | +0.012% | +0.016% | +0.200% | -0.189% | 51% | 48% | 54% | 10 pts |
| pullback from 10:00 | nv_b | 27 | -0.034% | -0.088% | -0.098% | +0.183% | -0.277% | 33% | 26% | 41% | 19 pts |
| control (random) | Default (Oct 27) | 133 | +0.027% | +0.032% | -0.001% | +0.244% | -0.218% | 50% | 45% | 43% | 9 pts |
| control (random) | nv_a | 199 | +0.017% | +0.021% | -0.008% | +0.245% | -0.226% | 50% | 50% | 51% | 7 pts |
| control (random) | nv_b | 103 | -0.058% | -0.029% | -0.098% | +0.226% | -0.272% | 38% | 48% | 42% | 10 pts |
| control before 10:00 | Default (Oct 27) | 22 | +0.078% | +0.111% | +0.090% | +0.344% | -0.230% | 41% | 41% | 45% | 21 pts |
| control before 10:00 | nv_a | 35 | +0.178% | +0.175% | +0.107% | +0.450% | -0.196% | 74% | 57% | 51% | 17 pts |
| control before 10:00 | nv_b | 27 | -0.093% | -0.106% | -0.304% | +0.268% | -0.385% | 33% | 41% | 33% | 19 pts |
| control from 10:00 | Default (Oct 27) | 111 | +0.016% | +0.016% | -0.019% | +0.224% | -0.215% | 51% | 46% | 42% | 9 pts |
| control from 10:00 | nv_a | 164 | -0.017% | -0.012% | -0.032% | +0.201% | -0.232% | 45% | 48% | 51% | 8 pts |
| control from 10:00 | nv_b | 76 | -0.045% | -0.001% | -0.025% | +0.211% | -0.232% | 39% | 50% | 45% | 11 pts |

### SPY every day

| Group | Run | Count | Avg 5m | Avg 10m | Avg 30m | Best 10m | Worst 10m | In favour 5m | 10m | 30m | Noise (±) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze (all) | all three runs | 50 | -0.021% | -0.001% | -0.024% | +0.088% | -0.103% | 46% | 54% | 46% | 14 pts |
| squeeze long | all three runs | 25 | -0.010% | +0.015% | -0.018% | +0.084% | -0.090% | 52% | 64% | 48% | 20 pts |
| squeeze short | all three runs | 25 | -0.032% | -0.018% | -0.030% | +0.093% | -0.116% | 40% | 44% | 44% | 20 pts |
| pullback (all) | Default (Oct 27) | 73 | -0.003% | -0.014% | -0.022% | +0.076% | -0.094% | 47% | 47% | 52% | 12 pts |
| pullback (all) | nv_a | 163 | -0.006% | -0.007% | -0.005% | +0.090% | -0.099% | 44% | 47% | 53% | 8 pts |
| pullback (all) | nv_b | 42 | +0.004% | -0.033% | -0.025% | +0.079% | -0.100% | 45% | 38% | 52% | 15 pts |
| pullback long | Default (Oct 27) | 43 | -0.004% | -0.011% | -0.013% | +0.070% | -0.089% | 44% | 49% | 53% | 15 pts |
| pullback long | nv_a | 84 | -0.008% | -0.008% | +0.003% | +0.081% | -0.097% | 46% | 54% | 55% | 11 pts |
| pullback long | nv_b | 21 | +0.003% | -0.013% | +0.021% | +0.069% | -0.079% | 52% | 43% | 67% | 22 pts |
| pullback short | Default (Oct 27) | 30 | -0.000% | -0.019% | -0.036% | +0.085% | -0.100% | 50% | 43% | 50% | 18 pts |
| pullback short | nv_a | 79 | -0.004% | -0.007% | -0.014% | +0.098% | -0.101% | 41% | 41% | 51% | 11 pts |
| pullback short | nv_b | 21 | +0.004% | -0.053% | -0.072% | +0.090% | -0.121% | 38% | 33% | 38% | 22 pts |
| pullback before 10:00 | Default (Oct 27) | 0 | - | - | - | - | - | - | - | - | - |
| pullback before 10:00 | nv_a | 32 | +0.007% | -0.023% | -0.022% | +0.118% | -0.135% | 44% | 50% | 47% | 18 pts |
| pullback before 10:00 | nv_b | 5 | +0.000% | -0.165% | -0.092% | +0.131% | -0.204% | 20% | 0% | 40% | 45 pts |
| pullback from 10:00 | Default (Oct 27) | 73 | -0.003% | -0.014% | -0.022% | +0.076% | -0.094% | 47% | 47% | 52% | 12 pts |
| pullback from 10:00 | nv_a | 131 | -0.009% | -0.004% | -0.001% | +0.083% | -0.090% | 44% | 47% | 54% | 9 pts |
| pullback from 10:00 | nv_b | 37 | +0.004% | -0.015% | -0.016% | +0.072% | -0.086% | 49% | 43% | 54% | 16 pts |
| control (random) | Default (Oct 27) | 123 | -0.001% | -0.007% | -0.008% | +0.088% | -0.092% | 52% | 51% | 55% | 9 pts |
| control (random) | nv_a | 213 | +0.005% | +0.003% | +0.021% | +0.088% | -0.080% | 53% | 51% | 53% | 7 pts |
| control (random) | nv_b | 92 | -0.005% | +0.006% | -0.008% | +0.086% | -0.086% | 38% | 52% | 50% | 10 pts |
| control before 10:00 | Default (Oct 27) | 25 | +0.015% | +0.012% | +0.032% | +0.111% | -0.094% | 52% | 48% | 64% | 20 pts |
| control before 10:00 | nv_a | 42 | +0.026% | +0.000% | +0.060% | +0.110% | -0.094% | 64% | 60% | 67% | 15 pts |
| control before 10:00 | nv_b | 20 | -0.009% | -0.036% | -0.009% | +0.097% | -0.125% | 30% | 35% | 55% | 22 pts |
| control from 10:00 | Default (Oct 27) | 98 | -0.005% | -0.012% | -0.018% | +0.082% | -0.092% | 52% | 52% | 53% | 10 pts |
| control from 10:00 | nv_a | 171 | -0.000% | +0.004% | +0.012% | +0.082% | -0.076% | 50% | 49% | 50% | 8 pts |
| control from 10:00 | nv_b | 72 | -0.004% | +0.018% | -0.007% | +0.083% | -0.075% | 40% | 57% | 49% | 12 pts |

## Options backtest (for information), ATR pick, 2026-06-01 to 2026-10-23

The current default was rerun with the new code: its 83 trades are identical to the October 27 run.

| Run | Trades | Wins | Total P&L | Best trade | Total without best | Before 10:00 | From 10:00 |
|---|---|---|---|---|---|---|---|
| Default | 83 | 32 | $-393.07 | $+346.00 (2026-09-03 QQQ squeeze) | $-739.07 | 3 trades, $+28.50 | 80 trades, $-421.57 |
| nv_a | 119 | 50 | $-285.11 | $+346.00 (2026-09-03 QQQ squeeze) | $-631.11 | 14 trades, $-263.60 | 105 trades, $-21.51 |
| nv_b | 60 | 22 | $-242.74 | $+346.00 (2026-09-03 QQQ squeeze) | $-588.74 | 7 trades, $-75.20 | 53 trades, $-167.54 |

| Setup | Default | nv_a | nv_b |
|---|---|---|---|
| pullback | 42: $-412.58 | 78: $-304.62 | 18: $-204.33 |
| squeeze | 41: $+19.51 | 41: $+19.51 | 42: $-38.41 |

| Exit reason | Default | nv_a | nv_b |
|---|---|---|---|
| hard_stop | 6: $-378.62 | 9: $-593.43 | 2: $-148.71 |
| noon_shutdown | 1: $+346.00 | 1: $+346.00 | 1: $+346.00 |
| profit_target | 1: $+146.22 | 4: $+555.63 | 1: $+86.77 |
| setup_failed | 4: $-136.44 | 6: $-170.94 | 1: $-41.86 |
| trailing_stop | 41: $-392.37 | 48: $-609.65 | 44: $-528.40 |
| volume_faded | 30: $+22.14 | 51: $+187.28 | 11: $+43.46 |

Cells are trades: total P&L.

## Default (squeeze only before 10:00, VWAP)

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

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 44 | 34.1% | $+8.94 | $+0.20 |
| short | 39 | 43.6% | $-402.01 | $-10.31 |

### Entries before 10:00

3 trades, win rate 66.7%, total $+28.50.

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00397500 | 09:35 | 3.21 | 09:36 | 2.79 | trailing_stop | $-42.00 |
| 2 | 2026-06-22 | TSLA | long | squeeze | TSLA260622C00400000 | 09:38 | 3.06 | 09:40 | 3.29 | trailing_stop | $+23.28 |
| 3 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.68 | 10:13 | 1.32 | hard_stop | $-36.35 |
| 2 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.42 | 10:46 | 2.74 | trailing_stop | $+32.66 |
| 3 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 6.01 | 10:48 | 6.40 | volume_faded | $+39.16 |
| 4 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 10:34 | 3.21 | 10:36 | 2.99 | volume_faded | $-22.40 |
| 5 | 2026-06-15 | TSLA | short | pullback | TSLA260615P00410000 | 11:47 | 2.92 | 11:48 | 2.28 | hard_stop | $-63.38 |
| 6 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.59 | 10:57 | 2.26 | volume_faded | $-32.70 |
| 7 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00397500 | 09:35 | 3.21 | 09:36 | 2.79 | trailing_stop | $-42.00 |
| 8 | 2026-06-22 | TSLA | long | squeeze | TSLA260622C00400000 | 09:38 | 3.06 | 09:40 | 3.29 | trailing_stop | $+23.28 |
| 9 | 2026-06-22 | TSLA | long | pullback | TSLA260622C00410000 | 11:44 | 2.61 | 11:45 | 2.29 | volume_faded | $-31.80 |
| 10 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.11 | 11:55 | 1.66 | trailing_stop | $-45.61 |
| 11 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.48 | 11:19 | 1.32 | trailing_stop | $-16.19 |
| 12 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 10:43 | 1.97 | 10:43 | 1.54 | trailing_stop | $-42.52 |
| 13 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 11:08 | 2.28 | 11:11 | 1.97 | trailing_stop | $-31.70 |
| 14 | 2026-06-29 | TSLA | long | pullback | TSLA260629C00392500 | 10:26 | 3.11 | 10:28 | 4.57 | profit_target | $+146.22 |
| 15 | 2026-06-29 | TSLA | long | squeeze | TSLA260629C00400000 | 11:28 | 1.52 | 11:28 | 1.19 | trailing_stop | $-32.83 |
| 16 | 2026-06-30 | QQQ | long | squeeze | QQQ260630C00734000 | 11:35 | 1.49 | 11:38 | 1.17 | trailing_stop | $-32.10 |
| 17 | 2026-07-01 | TSLA | long | squeeze | TSLA260701C00430000 | 10:48 | 1.78 | 10:50 | 1.72 | trailing_stop | $-7.00 |
| 18 | 2026-07-07 | QQQ | long | squeeze | QQQ260707C00708000 | 11:45 | 1.73 | 11:49 | 1.87 | trailing_stop | $+13.19 |
| 19 | 2026-07-08 | TSLA | long | squeeze | TSLA260708C00397500 | 10:22 | 1.98 | 10:26 | 2.23 | trailing_stop | $+24.78 |
| 20 | 2026-07-10 | TSLA | long | squeeze | TSLA260710C00410000 | 11:17 | 1.42 | 11:19 | 1.22 | trailing_stop | $-19.48 |
| 21 | 2026-07-13 | TSLA | short | squeeze | TSLA260713P00392500 | 10:17 | 1.95 | 10:18 | 1.93 | trailing_stop | $-1.96 |
| 22 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.49 | 11:49 | 2.74 | volume_faded | $+25.52 |
| 23 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:18 | 4.17 | volume_faded | $+40.08 |
| 24 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:57 | 1.78 | trailing_stop | $-15.83 |
| 25 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.86 | 11:27 | 1.81 | volume_faded | $-4.34 |
| 26 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.84 | 11:42 | 3.15 | volume_faded | $+31.02 |
| 27 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.62 | 10:11 | 2.63 | volume_faded | $+0.50 |
| 28 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.83 | 10:36 | 2.84 | volume_faded | $+1.66 |
| 29 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:31 | 2.29 | trailing_stop | $+18.81 |
| 30 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:21 | 2.39 | trailing_stop | $-65.88 |
| 31 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:20 | 3.11 | volume_faded | $+0.58 |
| 32 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.41 | 11:16 | 1.89 | hard_stop | $-52.00 |
| 33 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.98 | 10:46 | 1.85 | volume_faded | $-12.66 |
| 34 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 10:58 | 1.54 | trailing_stop | $+0.66 |
| 35 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.91 | 10:22 | 1.94 | volume_faded | $+3.30 |
| 36 | 2026-08-10 | TSLA | long | squeeze | TSLA260810C00332500 | 10:27 | 1.11 | 10:33 | 1.11 | trailing_stop | $-0.44 |
| 37 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.59 | 11:24 | 1.27 | setup_failed | $-31.72 |
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
| 56 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 10:52 | 0.78 | trailing_stop | $-16.22 |
| 57 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.95 | 10:58 | 0.87 | trailing_stop | $-7.84 |
| 58 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:28 | 1.13 | volume_faded | $-17.86 |
| 59 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:37 | 1.38 | trailing_stop | $-10.94 |
| 60 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.55 | 11:37 | 1.77 | volume_faded | $+22.34 |
| 61 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.13 | 10:18 | 2.31 | volume_faded | $+18.10 |
| 62 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 10:18 | 1.59 | trailing_stop | $+33.69 |
| 63 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.30 | 11:15 | 1.12 | setup_failed | $-17.82 |
| 64 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.68 | 11:34 | 1.40 | setup_failed | $-28.16 |
| 65 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.80 | 10:15 | 1.97 | volume_faded | $+17.46 |
| 66 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 10:57 | 2.63 | trailing_stop | $-65.80 |
| 67 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:49 | 2.27 | trailing_stop | $-44.98 |
| 68 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 11:37 | 3.53 | trailing_stop | $+6.00 |
| 69 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.23 | 10:44 | 3.65 | setup_failed | $-58.74 |
| 70 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 4.05 | 11:22 | 3.09 | hard_stop | $-96.24 |
| 71 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.70 | trailing_stop | $-46.93 |
| 72 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:53 | 1.63 | trailing_stop | $-14.41 |
| 73 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00742000 | 11:20 | 1.24 | 11:22 | 1.22 | volume_faded | $-2.92 |
| 74 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.66 | 10:08 | 5.24 | volume_faded | $-41.80 |
| 75 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:13 | 2.90 | trailing_stop | $+25.90 |
| 76 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 11:40 | 2.69 | trailing_stop | $+7.40 |
| 77 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 78 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.93 | 11:48 | 3.08 | hard_stop | $-84.82 |
| 79 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 10:44 | 3.21 | trailing_stop | $-5.98 |
| 80 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.25 | 11:47 | 2.00 | volume_faded | $-25.50 |
| 81 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 4.03 | 10:42 | 4.21 | volume_faded | $+18.50 |
| 82 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.52 | 10:51 | 4.04 | volume_faded | $-48.10 |
| 83 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:24 | 2.56 | trailing_stop | $-52.26 |

## nv_a (no VWAP, all rules from 9:35, chop filter off)

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 119 | 42.0% | $+39.57 | $-32.80 | $-285.11 | $-2.40 | $+346.00 | $-135.50 | $+356.76 | $-245.73 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 41 | 36.6% | $+19.51 | $+0.48 |
| pullback | 78 | 44.9% | $-304.62 | $-3.91 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 45 | 46.7% | $+313.44 | $+6.97 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| TSLA | 50 | 38.0% | $-209.08 | $-4.18 |
| META | 23 | 43.5% | $-353.12 | $-15.35 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 4 | 100.0% | $+555.63 | $+138.91 |
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| volume_faded | 51 | 58.8% | $+187.28 | $+3.67 |
| setup_failed | 6 | 0.0% | $-170.94 | $-28.49 |
| hard_stop | 9 | 0.0% | $-593.43 | $-65.94 |
| trailing_stop | 48 | 31.2% | $-609.65 | $-12.70 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 59 | 32.2% | $-31.60 | $-0.54 |
| short | 60 | 51.7% | $-253.51 | $-4.23 |

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
| 18 | 2026-06-29 | TSLA | short | pullback | TSLA260629P00397500 | 11:16 | 2.99 | 11:17 | 3.02 | volume_faded | $+2.98 |
| 19 | 2026-06-29 | TSLA | long | squeeze | TSLA260629C00400000 | 11:28 | 1.52 | 11:28 | 1.19 | trailing_stop | $-32.83 |
| 20 | 2026-06-30 | QQQ | long | squeeze | QQQ260630C00734000 | 11:35 | 1.49 | 11:38 | 1.17 | trailing_stop | $-32.10 |
| 21 | 2026-07-01 | TSLA | short | pullback | TSLA260701P00427500 | 10:34 | 4.03 | 10:35 | 3.67 | volume_faded | $-35.40 |
| 22 | 2026-07-01 | TSLA | long | squeeze | TSLA260701C00430000 | 10:48 | 1.78 | 10:50 | 1.72 | trailing_stop | $-7.00 |
| 23 | 2026-07-06 | TSLA | short | pullback | TSLA260706P00392500 | 09:37 | 4.31 | 09:39 | 3.81 | trailing_stop | $-50.91 |
| 24 | 2026-07-07 | QQQ | long | squeeze | QQQ260707C00708000 | 11:45 | 1.73 | 11:49 | 1.87 | trailing_stop | $+13.19 |
| 25 | 2026-07-08 | TSLA | long | squeeze | TSLA260708C00397500 | 10:22 | 1.98 | 10:26 | 2.23 | trailing_stop | $+24.78 |
| 26 | 2026-07-10 | TSLA | long | squeeze | TSLA260710C00410000 | 11:17 | 1.42 | 11:19 | 1.22 | trailing_stop | $-19.48 |
| 27 | 2026-07-13 | TSLA | short | squeeze | TSLA260713P00392500 | 10:17 | 1.95 | 10:18 | 1.93 | trailing_stop | $-1.96 |
| 28 | 2026-07-13 | TSLA | short | pullback | TSLA260713P00397500 | 11:48 | 2.49 | 11:49 | 2.74 | volume_faded | $+25.52 |
| 29 | 2026-07-14 | QQQ | short | pullback | QQQ260714P00721000 | 11:42 | 1.80 | 11:44 | 1.76 | trailing_stop | $-3.59 |
| 30 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:18 | 4.17 | volume_faded | $+40.08 |
| 31 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:57 | 1.78 | trailing_stop | $-15.83 |
| 32 | 2026-07-16 | QQQ | long | pullback | QQQ260716C00711000 | 11:26 | 1.86 | 11:27 | 1.81 | volume_faded | $-4.34 |
| 33 | 2026-07-20 | TSLA | short | pullback | TSLA260720P00375000 | 11:36 | 2.84 | 11:42 | 3.15 | volume_faded | $+31.02 |
| 34 | 2026-07-21 | QQQ | short | pullback | QQQ260721P00704000 | 10:09 | 2.62 | 10:11 | 2.63 | volume_faded | $+0.50 |
| 35 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:33 | 2.83 | 10:36 | 2.84 | volume_faded | $+1.66 |
| 36 | 2026-07-23 | QQQ | short | pullback | QQQ260723P00694000 | 10:43 | 2.96 | 10:44 | 3.10 | volume_faded | $+13.88 |
| 37 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:31 | 2.29 | trailing_stop | $+18.81 |
| 38 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:21 | 2.39 | trailing_stop | $-65.88 |
| 39 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:20 | 3.11 | volume_faded | $+0.58 |
| 40 | 2026-07-31 | TSLA | long | pullback | TSLA260731C00307500 | 11:16 | 2.41 | 11:16 | 1.89 | hard_stop | $-52.00 |
| 41 | 2026-08-04 | QQQ | long | pullback | QQQ260804C00716000 | 10:45 | 1.98 | 10:46 | 1.85 | volume_faded | $-12.66 |
| 42 | 2026-08-05 | TSLA | long | pullback | TSLA260805C00325000 | 09:42 | 3.26 | 09:42 | 2.56 | hard_stop | $-70.50 |
| 43 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 10:58 | 1.54 | trailing_stop | $+0.66 |
| 44 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 10:21 | 1.91 | 10:22 | 1.94 | volume_faded | $+3.30 |
| 45 | 2026-08-10 | TSLA | long | squeeze | TSLA260810C00332500 | 10:27 | 1.11 | 10:33 | 1.11 | trailing_stop | $-0.44 |
| 46 | 2026-08-10 | TSLA | long | pullback | TSLA260810C00330000 | 11:22 | 1.59 | 11:24 | 1.27 | setup_failed | $-31.72 |
| 47 | 2026-08-11 | QQQ | long | pullback | QQQ260811C00721000 | 10:12 | 2.02 | 10:13 | 1.98 | volume_faded | $-4.00 |
| 48 | 2026-08-11 | QQQ | short | pullback | QQQ260811P00722000 | 11:06 | 1.57 | 11:10 | 2.23 | volume_faded | $+66.36 |
| 49 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.92 | 10:37 | 1.66 | trailing_stop | $+74.41 |
| 50 | 2026-08-13 | QQQ | short | pullback | QQQ260813P00733000 | 11:09 | 1.83 | 11:10 | 1.52 | setup_failed | $-30.68 |
| 51 | 2026-08-13 | QQQ | long | pullback | QQQ260813C00732000 | 11:14 | 1.88 | 11:15 | 1.67 | volume_faded | $-21.08 |
| 52 | 2026-08-17 | TSLA | long | pullback | TSLA260817C00337500 | 10:36 | 3.20 | 10:37 | 3.38 | volume_faded | $+17.82 |
| 53 | 2026-08-17 | TSLA | short | pullback | TSLA260817P00342500 | 11:33 | 2.76 | 11:37 | 3.09 | volume_faded | $+32.28 |
| 54 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.87 | 10:12 | 2.11 | volume_faded | $+24.04 |
| 55 | 2026-08-18 | QQQ | long | pullback | QQQ260818C00717000 | 11:24 | 1.54 | 11:25 | 1.55 | volume_faded | $+0.82 |
| 56 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.75 | 10:42 | 2.50 | volume_faded | $-25.50 |
| 57 | 2026-08-19 | META | long | squeeze | META260819C00550000 | 10:47 | 1.96 | 11:01 | 2.05 | trailing_stop | $+9.57 |
| 58 | 2026-08-21 | META | long | pullback | META260821C00550000 | 10:09 | 3.31 | 10:10 | 3.33 | volume_faded | $+1.70 |
| 59 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.68 | 10:58 | 2.04 | trailing_stop | $+35.54 |
| 60 | 2026-08-21 | META | short | pullback | META260821P00550000 | 11:43 | 2.36 | 11:44 | 2.58 | volume_faded | $+22.12 |
| 61 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.85 | 11:29 | 0.66 | trailing_stop | $-18.29 |
| 62 | 2026-08-25 | QQQ | short | pullback | QQQ260825P00710000 | 11:02 | 1.74 | 11:03 | 1.69 | volume_faded | $-5.86 |
| 63 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 2.01 | 10:20 | 1.65 | trailing_stop | $-36.30 |
| 64 | 2026-08-26 | TSLA | short | pullback | TSLA260826P00350000 | 10:23 | 3.44 | 10:29 | 4.41 | volume_faded | $+97.26 |
| 65 | 2026-08-27 | QQQ | long | pullback | QQQ260827C00717000 | 10:08 | 2.12 | 10:08 | 1.66 | hard_stop | $-45.83 |
| 66 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.47 | 10:42 | 1.15 | trailing_stop | $-31.73 |
| 67 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.18 | 10:41 | 0.96 | trailing_stop | $-22.67 |
| 68 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.39 | 10:18 | 2.21 | trailing_stop | $-17.59 |
| 69 | 2026-08-31 | TSLA | long | pullback | TSLA260831C00362500 | 11:44 | 3.26 | 11:48 | 3.97 | volume_faded | $+70.50 |
| 70 | 2026-09-01 | QQQ | long | pullback | QQQ260901C00708000 | 10:16 | 1.74 | 10:17 | 1.57 | volume_faded | $-17.62 |
| 71 | 2026-09-02 | TSLA | short | pullback | TSLA260902P00355000 | 09:37 | 3.40 | 09:40 | 3.99 | trailing_stop | $+59.78 |
| 72 | 2026-09-03 | QQQ | long | pullback | QQQ260903C00711000 | 09:38 | 1.85 | 09:39 | 2.71 | profit_target | $+86.77 |
| 73 | 2026-09-03 | QQQ | short | pullback | QQQ260903P00712000 | 10:02 | 2.04 | 10:03 | 1.60 | trailing_stop | $-44.06 |
| 74 | 2026-09-03 | QQQ | long | pullback | QQQ260903C00712000 | 10:56 | 1.48 | 10:56 | 1.16 | hard_stop | $-31.95 |
| 75 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.23 | 12:00 | 4.69 | noon_shutdown | $+346.00 |
| 76 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 77 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 10:52 | 0.78 | trailing_stop | $-16.22 |
| 78 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.95 | 10:58 | 0.87 | trailing_stop | $-7.84 |
| 79 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:28 | 1.13 | volume_faded | $-17.86 |
| 80 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:37 | 1.38 | trailing_stop | $-10.94 |
| 81 | 2026-09-09 | TSLA | long | pullback | TSLA260909C00372500 | 10:47 | 2.60 | 10:49 | 2.57 | volume_faded | $-3.34 |
| 82 | 2026-09-10 | QQQ | short | pullback | QQQ260910P00712000 | 11:17 | 2.01 | 11:18 | 2.19 | volume_faded | $+17.60 |
| 83 | 2026-09-10 | QQQ | long | pullback | QQQ260910C00711000 | 11:36 | 1.55 | 11:37 | 1.77 | volume_faded | $+22.34 |
| 84 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00362500 | 09:37 | 3.21 | 09:40 | 3.07 | volume_faded | $-14.56 |
| 85 | 2026-09-14 | TSLA | short | pullback | TSLA260914P00360000 | 10:17 | 2.13 | 10:18 | 2.31 | volume_faded | $+18.10 |
| 86 | 2026-09-14 | TSLA | long | pullback | TSLA260914C00357500 | 11:06 | 2.56 | 11:08 | 2.34 | volume_faded | $-21.80 |
| 87 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 10:18 | 1.59 | trailing_stop | $+33.69 |
| 88 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00705000 | 11:14 | 1.30 | 11:15 | 1.12 | setup_failed | $-17.82 |
| 89 | 2026-09-15 | QQQ | short | pullback | QQQ260915P00706000 | 11:33 | 1.68 | 11:34 | 1.40 | setup_failed | $-28.16 |
| 90 | 2026-09-15 | QQQ | long | pullback | QQQ260915C00705000 | 11:42 | 1.47 | 11:45 | 1.33 | volume_faded | $-13.60 |
| 91 | 2026-09-22 | QQQ | long | pullback | QQQ260922C00745000 | 10:12 | 1.80 | 10:15 | 1.97 | volume_faded | $+17.46 |
| 92 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 10:57 | 2.63 | trailing_stop | $-65.80 |
| 93 | 2026-09-23 | META | long | pullback | META260923C00750000 | 11:16 | 4.75 | 11:20 | 6.99 | profit_target | $+223.40 |
| 94 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:49 | 2.27 | trailing_stop | $-44.98 |
| 95 | 2026-09-29 | QQQ | long | pullback | QQQ260929C00738000 | 10:17 | 2.17 | 10:18 | 2.20 | volume_faded | $+2.26 |
| 96 | 2026-09-29 | QQQ | short | pullback | QQQ260929P00738000 | 11:19 | 1.86 | 11:21 | 1.96 | volume_faded | $+10.36 |
| 97 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 11:37 | 3.53 | trailing_stop | $+6.00 |
| 98 | 2026-10-01 | QQQ | short | pullback | QQQ261001P00742000 | 09:44 | 2.70 | 09:45 | 2.74 | volume_faded | $+4.10 |
| 99 | 2026-10-01 | QQQ | short | pullback | QQQ261001P00740000 | 10:01 | 2.69 | 10:02 | 3.24 | volume_faded | $+55.10 |
| 100 | 2026-10-02 | META | long | pullback | META261002C00732500 | 10:42 | 4.23 | 10:45 | 3.63 | volume_faded | $-60.70 |
| 101 | 2026-10-02 | META | short | pullback | META261002P00732500 | 11:21 | 4.05 | 11:22 | 3.09 | hard_stop | $-96.24 |
| 102 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.70 | trailing_stop | $-46.93 |
| 103 | 2026-10-02 | META | long | pullback | META261002C00730000 | 11:34 | 3.93 | 11:35 | 3.51 | setup_failed | $-41.86 |
| 104 | 2026-10-06 | QQQ | short | pullback | QQQ261006P00763000 | 11:29 | 1.37 | 11:32 | 1.42 | volume_faded | $+5.42 |
| 105 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:53 | 1.63 | trailing_stop | $-14.41 |
| 106 | 2026-10-13 | QQQ | short | pullback | QQQ261013P00744000 | 10:17 | 1.74 | 10:18 | 1.75 | volume_faded | $+1.00 |
| 107 | 2026-10-13 | QQQ | long | pullback | QQQ261013C00741000 | 11:19 | 1.53 | 11:20 | 1.32 | setup_failed | $-20.70 |
| 108 | 2026-10-14 | META | short | pullback | META261014P00750000 | 10:07 | 5.66 | 10:08 | 5.24 | volume_faded | $-41.80 |
| 109 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:13 | 2.90 | trailing_stop | $+25.90 |
| 110 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 11:40 | 2.69 | trailing_stop | $+7.40 |
| 111 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 112 | 2026-10-16 | META | short | pullback | META261016P00722500 | 11:47 | 3.93 | 11:48 | 3.08 | hard_stop | $-84.82 |
| 113 | 2026-10-19 | META | short | pullback | META261019P00702500 | 09:39 | 6.27 | 09:40 | 4.92 | trailing_stop | $-135.50 |
| 114 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 10:44 | 3.21 | trailing_stop | $-5.98 |
| 115 | 2026-10-20 | QQQ | short | pullback | QQQ261020P00722000 | 11:10 | 2.11 | 11:12 | 3.10 | profit_target | $+99.24 |
| 116 | 2026-10-22 | QQQ | short | pullback | QQQ261022P00708000 | 11:46 | 2.25 | 11:47 | 2.00 | volume_faded | $-25.50 |
| 117 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:41 | 4.03 | 10:42 | 4.21 | volume_faded | $+18.50 |
| 118 | 2026-10-23 | META | long | pullback | META261023C00645000 | 10:49 | 4.52 | 10:51 | 4.04 | volume_faded | $-48.10 |
| 119 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:24 | 2.56 | trailing_stop | $-52.26 |

## nv_b (no VWAP, all rules from 9:35, chop filter EMA 20)

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 60 | 36.7% | $+42.92 | $-31.23 | $-242.74 | $-4.05 | $+346.00 | $-112.36 | $+432.77 | $-88.79 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 42 | 35.7% | $-38.41 | $-0.91 |
| pullback | 18 | 38.9% | $-204.33 | $-11.35 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 15 | 40.0% | $+264.87 | $+17.66 |
| NVDA | 1 | 0.0% | $-36.35 | $-36.35 |
| META | 14 | 50.0% | $-129.56 | $-9.25 |
| TSLA | 30 | 30.0% | $-341.70 | $-11.39 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+86.77 | $+86.77 |
| volume_faded | 11 | 54.5% | $+43.46 | $+3.95 |
| setup_failed | 1 | 0.0% | $-41.86 | $-41.86 |
| hard_stop | 2 | 0.0% | $-148.71 | $-74.36 |
| trailing_stop | 44 | 31.8% | $-528.40 | $-12.01 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| long | 30 | 26.7% | $-35.80 | $-1.19 |
| short | 30 | 46.7% | $-206.94 | $-6.90 |

### Entries before 10:00

7 trades, win rate 42.9%, total $-75.20.

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-10 | TSLA | long | pullback | TSLA260610C00395000 | 09:39 | 5.20 | 09:40 | 4.08 | hard_stop | $-112.36 |
| 2 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00397500 | 09:35 | 3.21 | 09:36 | 2.79 | trailing_stop | $-42.00 |
| 3 | 2026-06-22 | TSLA | long | squeeze | TSLA260622C00400000 | 09:38 | 3.06 | 09:40 | 3.29 | trailing_stop | $+23.28 |
| 4 | 2026-07-06 | TSLA | short | pullback | TSLA260706P00392500 | 09:37 | 4.31 | 09:39 | 3.81 | trailing_stop | $-50.91 |
| 5 | 2026-09-03 | QQQ | long | pullback | QQQ260903C00711000 | 09:38 | 1.85 | 09:39 | 2.71 | profit_target | $+86.77 |
| 6 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 7 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-06-05 | NVDA | short | pullback | NVDA260605P00212500 | 10:13 | 1.68 | 10:13 | 1.32 | hard_stop | $-36.35 |
| 2 | 2026-06-10 | TSLA | long | pullback | TSLA260610C00395000 | 09:39 | 5.20 | 09:40 | 4.08 | hard_stop | $-112.36 |
| 3 | 2026-06-10 | TSLA | short | squeeze | TSLA260610P00387500 | 10:43 | 2.42 | 10:46 | 2.74 | trailing_stop | $+32.66 |
| 4 | 2026-06-12 | TSLA | short | pullback | TSLA260612P00395000 | 10:44 | 6.01 | 10:48 | 6.40 | volume_faded | $+39.16 |
| 5 | 2026-06-16 | QQQ | short | pullback | QQQ260616P00738000 | 10:56 | 2.59 | 10:57 | 2.26 | volume_faded | $-32.70 |
| 6 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00397500 | 09:35 | 3.21 | 09:36 | 2.79 | trailing_stop | $-42.00 |
| 7 | 2026-06-22 | TSLA | long | squeeze | TSLA260622C00400000 | 09:38 | 3.06 | 09:40 | 3.29 | trailing_stop | $+23.28 |
| 8 | 2026-06-22 | TSLA | short | squeeze | TSLA260622P00407500 | 11:50 | 2.11 | 11:55 | 1.66 | trailing_stop | $-45.61 |
| 9 | 2026-06-24 | TSLA | long | squeeze | TSLA260624C00385000 | 11:17 | 1.48 | 11:19 | 1.32 | trailing_stop | $-16.19 |
| 10 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 10:43 | 1.97 | 10:43 | 1.54 | trailing_stop | $-42.52 |
| 11 | 2026-06-26 | TSLA | long | squeeze | TSLA260626C00380000 | 11:08 | 2.28 | 11:11 | 1.97 | trailing_stop | $-31.70 |
| 12 | 2026-06-29 | TSLA | long | squeeze | TSLA260629C00400000 | 11:28 | 1.52 | 11:28 | 1.19 | trailing_stop | $-32.83 |
| 13 | 2026-06-30 | QQQ | long | squeeze | QQQ260630C00734000 | 11:35 | 1.49 | 11:38 | 1.17 | trailing_stop | $-32.10 |
| 14 | 2026-07-01 | TSLA | short | pullback | TSLA260701P00427500 | 10:34 | 4.03 | 10:35 | 3.67 | volume_faded | $-35.40 |
| 15 | 2026-07-01 | TSLA | long | squeeze | TSLA260701C00430000 | 10:48 | 1.78 | 10:50 | 1.72 | trailing_stop | $-7.00 |
| 16 | 2026-07-06 | TSLA | short | pullback | TSLA260706P00392500 | 09:37 | 4.31 | 09:39 | 3.81 | trailing_stop | $-50.91 |
| 17 | 2026-07-07 | QQQ | long | squeeze | QQQ260707C00708000 | 11:45 | 1.73 | 11:49 | 1.87 | trailing_stop | $+13.19 |
| 18 | 2026-07-08 | TSLA | long | squeeze | TSLA260708C00397500 | 10:22 | 1.98 | 10:26 | 2.23 | trailing_stop | $+24.78 |
| 19 | 2026-07-10 | TSLA | long | squeeze | TSLA260710C00410000 | 11:17 | 1.42 | 11:19 | 1.22 | trailing_stop | $-19.48 |
| 20 | 2026-07-13 | TSLA | short | squeeze | TSLA260713P00392500 | 10:17 | 1.95 | 10:18 | 1.93 | trailing_stop | $-1.96 |
| 21 | 2026-07-15 | TSLA | short | pullback | TSLA260715P00400000 | 10:16 | 3.77 | 10:18 | 4.17 | volume_faded | $+40.08 |
| 22 | 2026-07-16 | QQQ | short | squeeze | QQQ260716P00710000 | 10:51 | 1.94 | 10:57 | 1.78 | trailing_stop | $-15.83 |
| 23 | 2026-07-23 | QQQ | short | squeeze | QQQ260723P00693000 | 10:34 | 2.77 | 10:37 | 2.20 | trailing_stop | $-57.92 |
| 24 | 2026-07-24 | TSLA | short | squeeze | TSLA260724P00312500 | 10:18 | 2.10 | 10:31 | 2.29 | trailing_stop | $+18.81 |
| 25 | 2026-07-24 | TSLA | short | pullback | TSLA260724P00310000 | 11:20 | 3.05 | 11:21 | 2.39 | trailing_stop | $-65.88 |
| 26 | 2026-07-28 | QQQ | short | pullback | QQQ260728P00669000 | 10:15 | 3.10 | 10:20 | 3.11 | volume_faded | $+0.58 |
| 27 | 2026-08-05 | TSLA | short | squeeze | TSLA260805P00322500 | 10:52 | 1.53 | 10:58 | 1.54 | trailing_stop | $+0.66 |
| 28 | 2026-08-10 | TSLA | long | squeeze | TSLA260810C00332500 | 10:27 | 1.11 | 10:33 | 1.11 | trailing_stop | $-0.44 |
| 29 | 2026-08-12 | TSLA | short | squeeze | TSLA260812P00325000 | 10:27 | 0.92 | 10:37 | 1.66 | trailing_stop | $+74.41 |
| 30 | 2026-08-17 | TSLA | short | pullback | TSLA260817P00342500 | 11:33 | 2.76 | 11:37 | 3.09 | volume_faded | $+32.28 |
| 31 | 2026-08-18 | QQQ | short | pullback | QQQ260818P00718000 | 10:11 | 1.87 | 10:12 | 2.11 | volume_faded | $+24.04 |
| 32 | 2026-08-19 | META | long | pullback | META260819C00547500 | 10:41 | 2.75 | 10:42 | 2.50 | volume_faded | $-25.50 |
| 33 | 2026-08-19 | META | long | squeeze | META260819C00550000 | 10:47 | 1.96 | 11:01 | 2.05 | trailing_stop | $+9.57 |
| 34 | 2026-08-21 | META | long | squeeze | META260821C00552500 | 10:53 | 1.68 | 10:58 | 2.04 | trailing_stop | $+35.54 |
| 35 | 2026-08-21 | META | short | pullback | META260821P00550000 | 11:43 | 2.36 | 11:44 | 2.58 | volume_faded | $+22.12 |
| 36 | 2026-08-24 | TSLA | short | squeeze | TSLA260824P00355000 | 11:28 | 0.85 | 11:29 | 0.66 | trailing_stop | $-18.29 |
| 37 | 2026-08-26 | TSLA | long | squeeze | TSLA260826C00350000 | 10:18 | 2.01 | 10:20 | 1.65 | trailing_stop | $-36.30 |
| 38 | 2026-08-27 | QQQ | short | squeeze | QQQ260827P00717000 | 10:40 | 1.47 | 10:42 | 1.15 | trailing_stop | $-31.73 |
| 39 | 2026-08-28 | TSLA | long | squeeze | TSLA260828C00355000 | 10:38 | 1.18 | 10:41 | 0.96 | trailing_stop | $-22.67 |
| 40 | 2026-08-31 | TSLA | long | squeeze | TSLA260831C00362500 | 10:17 | 2.39 | 10:18 | 2.21 | trailing_stop | $-17.59 |
| 41 | 2026-09-03 | QQQ | long | pullback | QQQ260903C00711000 | 09:38 | 1.85 | 09:39 | 2.71 | profit_target | $+86.77 |
| 42 | 2026-09-03 | QQQ | long | squeeze | QQQ260903C00713000 | 10:59 | 1.23 | 12:00 | 4.69 | noon_shutdown | $+346.00 |
| 43 | 2026-09-08 | QQQ | short | pullback | QQQ260908P00718000 | 09:43 | 2.31 | 09:45 | 2.03 | trailing_stop | $-27.20 |
| 44 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:51 | 0.94 | 10:52 | 0.78 | trailing_stop | $-16.22 |
| 45 | 2026-09-08 | QQQ | long | squeeze | QQQ260908C00719000 | 10:53 | 0.95 | 10:58 | 0.87 | trailing_stop | $-7.84 |
| 46 | 2026-09-08 | QQQ | long | pullback | QQQ260908C00720000 | 11:26 | 1.31 | 11:28 | 1.13 | volume_faded | $-17.86 |
| 47 | 2026-09-09 | TSLA | long | squeeze | TSLA260909C00375000 | 10:34 | 1.49 | 10:37 | 1.38 | trailing_stop | $-10.94 |
| 48 | 2026-09-09 | TSLA | long | pullback | TSLA260909C00372500 | 10:47 | 2.60 | 10:49 | 2.57 | volume_faded | $-3.34 |
| 49 | 2026-09-15 | QQQ | short | squeeze | QQQ260915P00708000 | 10:04 | 1.25 | 10:18 | 1.59 | trailing_stop | $+33.69 |
| 50 | 2026-09-23 | META | long | squeeze | META260923C00755000 | 10:54 | 3.28 | 10:57 | 2.63 | trailing_stop | $-65.80 |
| 51 | 2026-09-28 | META | short | squeeze | META260928P00717500 | 11:42 | 2.72 | 11:49 | 2.27 | trailing_stop | $-44.98 |
| 52 | 2026-09-30 | META | long | squeeze | META260930C00732500 | 11:34 | 3.47 | 11:37 | 3.53 | trailing_stop | $+6.00 |
| 53 | 2026-10-02 | META | short | squeeze | META261002P00727500 | 11:25 | 2.17 | 11:26 | 1.70 | trailing_stop | $-46.93 |
| 54 | 2026-10-02 | META | long | pullback | META261002C00730000 | 11:34 | 3.93 | 11:35 | 3.51 | setup_failed | $-41.86 |
| 55 | 2026-10-09 | TSLA | long | squeeze | TSLA261009C00387500 | 10:50 | 1.77 | 10:53 | 1.63 | trailing_stop | $-14.41 |
| 56 | 2026-10-14 | META | short | squeeze | META261014P00742500 | 11:05 | 2.64 | 11:13 | 2.90 | trailing_stop | $+25.90 |
| 57 | 2026-10-14 | META | short | squeeze | META261014P00740000 | 11:36 | 2.61 | 11:40 | 2.69 | trailing_stop | $+7.40 |
| 58 | 2026-10-16 | META | short | squeeze | META261016P00727500 | 09:59 | 3.20 | 10:00 | 3.67 | trailing_stop | $+47.22 |
| 59 | 2026-10-19 | META | long | squeeze | META261019C00700000 | 10:41 | 3.27 | 10:44 | 3.21 | trailing_stop | $-5.98 |
| 60 | 2026-10-23 | META | short | squeeze | META261023P00645000 | 11:24 | 3.08 | 11:24 | 2.56 | trailing_stop | $-52.26 |
