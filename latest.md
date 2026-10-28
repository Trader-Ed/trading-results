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

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| profit_target | 4 | 100.0% | $+555.63 | $+138.91 |
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| volume_faded | 51 | 58.8% | $+187.28 | $+3.67 |
| setup_failed | 6 | 0.0% | $-170.94 | $-28.49 |
| hard_stop | 9 | 0.0% | $-593.43 | $-65.94 |
| trailing_stop | 48 | 31.2% | $-609.65 | $-12.70 |

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

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| noon_shutdown | 1 | 100.0% | $+346.00 | $+346.00 |
| profit_target | 1 | 100.0% | $+86.77 | $+86.77 |
| volume_faded | 11 | 54.5% | $+43.46 | $+3.95 |
| setup_failed | 1 | 0.0% | $-41.86 | $-41.86 |
| hard_stop | 2 | 0.0% | $-148.71 | $-74.36 |
| trailing_stop | 44 | 31.8% | $-528.40 | $-12.01 |

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

---

Full per-trade tables: [history/2026-10-28-no-vwap-test.md](history/2026-10-28-no-vwap-test.md)
