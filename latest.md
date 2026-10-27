# Signal test, new default rulebook, 2026-01-02 to 2026-10-23 (run 2026-10-27)

Do the entry signals point the right way? For every signal from the rules (new default: entries 9:35 to
11:50, squeeze rule only before 10:00, VWAP warm-up to 10:00), the stock's move in the signal's direction
is compared with the same number of random entries (random direction) on the same days and names, in the
same window. Options, exits and slippage are not involved: this measures the stock only.

**Reading it.** At these sample sizes, a group's average move has a noise band of roughly +/-0.06 to
+/-0.19 percentage points (ATR pick) and +/-0.02 to +/-0.05 (SPY), two standard errors, and its share
in favour roughly +/-9 to +/-14 points around 50%. Every signal group, on both runs and at every horizon,
is inside that band: neither the squeeze nor the pullback signals move the stock our way more often or
further than random entries do over this period.

| Run | Group | Count | Avg 10m (+/- 2 s.e.) | In favour 10m | Avg 30m (+/- 2 s.e.) | In favour 30m |
|---|---|---|---|---|---|---|
| ATR pick | squeeze | 69 | -0.001% +/-0.085 | 51% +/-12 | +0.066% +/-0.191 | 55% +/-12 |
| ATR pick | pullback | 64 | -0.005% +/-0.088 | 48% +/-12 | -0.008% +/-0.096 | 52% +/-12 |
| ATR pick | all signals | 133 | -0.003% +/-0.061 | 50% +/-9 | +0.030% +/-0.109 | 53% +/-9 |
| ATR pick | control | 133 | +0.032% +/-0.064 | 45% +/-9 | -0.001% +/-0.095 | 43% +/-9 |
| SPY | squeeze | 50 | -0.001% +/-0.036 | 54% +/-14 | -0.024% +/-0.052 | 46% +/-14 |
| SPY | pullback | 73 | -0.014% +/-0.024 | 47% +/-12 | -0.022% +/-0.032 | 52% +/-12 |
| SPY | all signals | 123 | -0.009% +/-0.020 | 50% +/-9 | -0.023% +/-0.028 | 50% +/-9 |
| SPY | control | 123 | -0.007% +/-0.022 | 51% +/-9 | -0.008% +/-0.037 | 55% +/-9 |

## Signal test, ATR pick, 2026-01-02 to 2026-10-23

ATR pick, 2026-01-02 to 2026-10-23, rulebook rulebook.yaml: entry window 09:35 to 11:50, squeeze rule only before 10:00, VWAP warm-up 30 min.

Moves are the stock's move in the signal's direction (up for long, down for short), as a percent of the signal bar's close, at +5, +10 and +30 minutes after that bar closes; best and worst are the most favourable and most adverse move within 10 minutes. Repeats of the same setup and side within 5 minutes are skipped. The control group has one random entry time per signal, on the same day and name and in the same entry window, with a random direction (seed 7). Days with signals: 94.

| Group | Count | Avg 5m | Avg 10m | Avg 30m | Avg best 10m | Avg worst 10m | In favour 5m | In favour 10m | In favour 30m |
|---|---|---|---|---|---|---|---|---|---|
| squeeze (all) | 69 | -0.011% | -0.001% | +0.066% | +0.235% | -0.239% | 53.6% | 50.7% | 55.1% |
| squeeze long | 39 | +0.004% | +0.029% | +0.117% | +0.250% | -0.225% | 59.0% | 53.8% | 53.8% |
| squeeze short | 30 | -0.031% | -0.041% | -0.002% | +0.214% | -0.257% | 46.7% | 46.7% | 56.7% |
| pullback (all) | 64 | -0.010% | -0.005% | -0.008% | +0.213% | -0.222% | 50.0% | 48.4% | 51.6% |
| pullback long | 36 | -0.013% | -0.018% | -0.008% | +0.192% | -0.210% | 47.2% | 47.2% | 50.0% |
| pullback short | 28 | -0.005% | +0.013% | -0.007% | +0.239% | -0.239% | 53.6% | 50.0% | 53.6% |
| all signals | 133 | -0.010% | -0.003% | +0.030% | +0.224% | -0.231% | 51.9% | 49.6% | 53.4% |
| control (random) | 133 | +0.027% | +0.032% | -0.001% | +0.244% | -0.218% | 49.6% | 45.1% | 42.9% |

## Signal test, every day SPY, 2026-01-02 to 2026-10-23

every day SPY, 2026-01-02 to 2026-10-23, rulebook rulebook.yaml: entry window 09:35 to 11:50, squeeze rule only before 10:00, VWAP warm-up 30 min.

Moves are the stock's move in the signal's direction (up for long, down for short), as a percent of the signal bar's close, at +5, +10 and +30 minutes after that bar closes; best and worst are the most favourable and most adverse move within 10 minutes. Repeats of the same setup and side within 5 minutes are skipped. The control group has one random entry time per signal, on the same day and name and in the same entry window, with a random direction (seed 7). Days with signals: 93.

| Group | Count | Avg 5m | Avg 10m | Avg 30m | Avg best 10m | Avg worst 10m | In favour 5m | In favour 10m | In favour 30m |
|---|---|---|---|---|---|---|---|---|---|
| squeeze (all) | 50 | -0.021% | -0.001% | -0.024% | +0.088% | -0.103% | 46.0% | 54.0% | 46.0% |
| squeeze long | 25 | -0.010% | +0.015% | -0.018% | +0.084% | -0.090% | 52.0% | 64.0% | 48.0% |
| squeeze short | 25 | -0.032% | -0.018% | -0.030% | +0.093% | -0.116% | 40.0% | 44.0% | 44.0% |
| pullback (all) | 73 | -0.003% | -0.014% | -0.022% | +0.076% | -0.094% | 46.6% | 46.6% | 52.1% |
| pullback long | 43 | -0.004% | -0.011% | -0.013% | +0.070% | -0.089% | 44.2% | 48.8% | 53.5% |
| pullback short | 30 | -0.000% | -0.019% | -0.036% | +0.085% | -0.100% | 50.0% | 43.3% | 50.0% |
| all signals | 123 | -0.010% | -0.009% | -0.023% | +0.081% | -0.097% | 46.3% | 49.6% | 49.6% |
| control (random) | 123 | -0.001% | -0.007% | -0.008% | +0.088% | -0.092% | 52.0% | 51.2% | 55.3% |
---

Full per-trade tables: [history/2026-10-27-signal-test.md](history/2026-10-27-signal-test.md)
