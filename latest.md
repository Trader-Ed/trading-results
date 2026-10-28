# Ed's indicator rules V1: signal test series, October 28

Eight entry rules, each tested on its own. Only the rule being tested gives signals; the squeeze and pullback rules are off. The default rulebook.yaml is unchanged; each rule is a variant in variants/.

## Findings

- **No rule passes the gate.** On the ATR pick and on SPY, no rule moves the stock our way more often, or further, than random entries taken the same way, beyond the noise. This holds by side and at +5, +10, +30 and +60 minutes.
- **Why longs look good at first sight:** longs are 52–57% in favour at +30/+60 minutes for many rules, and shorts are 40–50%. Random times on the same days do the same (up to 56% for longs) because the market drifted up over the period.
  - That's why each rule is compared with the control "taken long" and "taken short".
  - The closest to an edge is e1_trend long: 55% in favour at +30 minutes against 52–53% for random longs, on both picks. That is within the ±4-point noise.
- **e1 races (stop vs 1.5×, 2× the risk and the 20-bar swing):** the e1 stop is tight (about 0.3% of price on the ATR pick, 0.12% on SPY).
  - Of the races that finished, the 1.5× target came first about 37–41% of the time and the 2× target about 28–33%. Random entries with the same distances did about the same: 37–42% and 29–35%.
  - That is roughly break-even before costs. The break-even rates are 40% for 1.5× and 33% for 2×.
  - The swing target came first in 58–69% of races, but it is closer than the stop for 76–86% of signals, and random entries did the same.
- **b3 races (reaching the opposite band within 60 minutes):**
  - After a 1-minute band touch, the opposite band was reached 43–48% of the time, with a median of 16–18 minutes. Random entries managed 47–48%, with a median of 15–17 minutes.
  - After a 1-minute re-entry it was 34–38%, against 34–42% for random entries.
  - After a 5-minute touch it was 14–16%, against 9–14%. The one gap, 5-minute shorts on the ATR pick (16% vs 9%), doesn't appear on SPY (14% vs 14%).
  - So there is no sign that band touches revert more than chance.
- **Signal counts are high.** Even with the 5-minute repeat rule, e1_reject and b3_touch_1m fire about 15–20 times a day. Same-day signals move together, so the noise bands here are computed by day, not by signal. They are wider than a per-signal count would suggest.

## Method

- **Window and period:** 2026-01-02 to 2026-10-23, entry window 9:35 to 11:50, 1-minute bars unless the rule name ends in 5m.
  - 5-minute bars are built from the 1-minute bars on clock boundaries. Each is decided at its close, on its last minute, with 300 minutes of the previous session kept for warm-up.
- **Definitions:** "rising" means higher than 3 bars ago. "Touch" means within 0.05% of the level, or through it.
  - A bar where a rule fires both ways gives no signal.
  - Repeats of the same rule and side within 5 minutes are skipped.
- **Moves** are in the signal's direction, in percent of the signal bar's close. Best and worst are within 10 minutes.
- **Control:** one random entry per signal, on the same day and name, in the same window, with a random direction (seed 7).
  - "Control taken long" counts every control entry as a buy, and "taken short" counts every one as a sale. This shows what the market's drift alone gives each side.
- **Noise (±, by day):** two standard errors of the in-favour share at +30 minutes, clustered by day.
- **e1 races, within 60 minutes:**
  - The stop is $0.05 beyond the lower of the 5-bar swing low and EMA 20 (the higher of the swing high and EMA 20 for shorts). Risk is the distance from the signal bar's close to the stop.
  - The targets are 1.5× and 2× the risk, and the prior 20-bar swing high (low for shorts). The swing race is skipped when price is already past that level.
  - Each target is raced against the stop on its own: target first, stop first, both in one bar, or neither within 60 minutes.
  - The control uses a random bar in the window on the same day, a random direction and the same $ distances.
- **b3 races:** the distance to the opposite Bollinger Band (20, 2) as it stood at entry, and the minutes until a bar reached it. The control uses a random bar and direction with the same distance.

## Signal test (the gate)

### ATR pick

| Rule | Group | Count | Avg 5m | Avg 10m | Avg 30m | Avg 60m | Best 10m | Worst 10m | In favour 5m | In favour 10m | In favour 30m | In favour 60m | Noise (±, by day) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| e1_trend | all | 1940 | +0.010% | +0.013% | +0.024% | +0.032% | +0.232% | -0.216% | 53% | 52% | 52% | 51% | 2 pts |
|  | long | 983 | +0.016% | +0.019% | +0.052% | +0.080% | +0.225% | -0.210% | 54% | 53% | 55% | 53% | 4 pts |
|  | control taken long | 1940 | +0.004% | +0.007% | +0.018% | +0.036% | - | - | 50% | 50% | 52% | 50% | 3 pts |
|  | short | 957 | +0.003% | +0.006% | -0.005% | -0.018% | +0.238% | -0.223% | 52% | 52% | 49% | 50% | 4 pts |
|  | control taken short | 1940 | -0.004% | -0.007% | -0.018% | -0.036% | - | - | 50% | 50% | 48% | 50% | 3 pts |
|  | control (random side) | 1940 | -0.007% | -0.011% | -0.019% | -0.024% | +0.231% | -0.237% | 50% | 48% | 47% | 49% | 2 pts |
| e1_reject | all | 3256 | +0.005% | +0.008% | +0.024% | +0.040% | +0.225% | -0.220% | 51% | 51% | 52% | 52% | 2 pts |
|  | long | 1704 | +0.011% | +0.017% | +0.044% | +0.077% | +0.221% | -0.211% | 52% | 54% | 55% | 53% | 4 pts |
|  | control taken long | 3256 | +0.001% | +0.005% | +0.013% | +0.032% | - | - | 50% | 51% | 52% | 52% | 3 pts |
|  | short | 1552 | -0.002% | -0.002% | +0.002% | -0.001% | +0.229% | -0.229% | 51% | 49% | 49% | 50% | 4 pts |
|  | control taken short | 3256 | -0.001% | -0.005% | -0.013% | -0.032% | - | - | 50% | 49% | 48% | 48% | 3 pts |
|  | control (random side) | 3256 | -0.002% | +0.002% | -0.005% | -0.008% | +0.223% | -0.223% | 49% | 51% | 49% | 50% | 2 pts |
| r2_rsi_1m | all | 493 | -0.011% | -0.008% | -0.025% | -0.017% | +0.262% | -0.278% | 49% | 47% | 46% | 50% | 5 pts |
|  | long | 316 | +0.005% | +0.008% | -0.011% | -0.016% | +0.274% | -0.264% | 51% | 48% | 49% | 52% | 6 pts |
|  | control taken long | 493 | -0.001% | +0.010% | +0.010% | +0.018% | - | - | 49% | 51% | 52% | 51% | 5 pts |
|  | short | 177 | -0.039% | -0.037% | -0.049% | -0.019% | +0.242% | -0.303% | 44% | 46% | 40% | 47% | 7 pts |
|  | control taken short | 493 | +0.001% | -0.010% | -0.010% | -0.018% | - | - | 50% | 49% | 48% | 48% | 5 pts |
|  | control (random side) | 493 | +0.006% | +0.008% | +0.020% | +0.039% | +0.236% | -0.233% | 49% | 51% | 52% | 51% | 5 pts |
| r2_rsi_5m | all | 276 | +0.015% | -0.011% | -0.068% | -0.047% | +0.259% | -0.257% | 54% | 46% | 43% | 45% | 7 pts |
|  | long | 189 | -0.011% | -0.030% | -0.088% | -0.043% | +0.231% | -0.271% | 50% | 45% | 42% | 46% | 9 pts |
|  | control taken long | 276 | -0.029% | -0.022% | -0.058% | -0.080% | - | - | 47% | 48% | 45% | 44% | 7 pts |
|  | short | 87 | +0.072% | +0.030% | -0.022% | -0.056% | +0.319% | -0.227% | 61% | 48% | 47% | 44% | 11 pts |
|  | control taken short | 276 | +0.029% | +0.022% | +0.058% | +0.080% | - | - | 53% | 52% | 55% | 56% | 7 pts |
|  | control (random side) | 276 | +0.005% | +0.014% | +0.022% | -0.010% | +0.235% | -0.235% | 49% | 49% | 53% | 49% | 6 pts |
| r2_rsi_1m_sym | all | 352 | -0.015% | -0.016% | -0.032% | -0.042% | +0.253% | -0.279% | 47% | 46% | 46% | 49% | 6 pts |
|  | long | 175 | +0.008% | +0.005% | -0.015% | -0.065% | +0.264% | -0.254% | 50% | 46% | 52% | 52% | 8 pts |
|  | control taken long | 352 | -0.011% | -0.025% | -0.022% | -0.014% | - | - | 47% | 47% | 49% | 50% | 7 pts |
|  | short | 177 | -0.039% | -0.037% | -0.049% | -0.019% | +0.242% | -0.303% | 44% | 46% | 40% | 47% | 7 pts |
|  | control taken short | 352 | +0.011% | +0.025% | +0.022% | +0.014% | - | - | 52% | 53% | 51% | 50% | 7 pts |
|  | control (random side) | 352 | +0.003% | +0.008% | +0.005% | -0.033% | +0.239% | -0.233% | 51% | 52% | 50% | 48% | 5 pts |
| b3_touch_1m | all | 3183 | +0.001% | -0.002% | -0.018% | -0.028% | +0.217% | -0.217% | 50% | 49% | 50% | 48% | 2 pts |
|  | long | 1560 | -0.000% | +0.001% | -0.004% | +0.007% | +0.221% | -0.224% | 51% | 51% | 52% | 51% | 4 pts |
|  | control taken long | 3183 | +0.002% | +0.006% | +0.019% | +0.034% | - | - | 50% | 52% | 52% | 53% | 3 pts |
|  | short | 1623 | +0.001% | -0.005% | -0.033% | -0.061% | +0.214% | -0.210% | 49% | 47% | 47% | 46% | 4 pts |
|  | control taken short | 3183 | -0.002% | -0.006% | -0.019% | -0.034% | - | - | 50% | 48% | 48% | 47% | 3 pts |
|  | control (random side) | 3183 | -0.000% | +0.003% | +0.001% | -0.005% | +0.218% | -0.219% | 50% | 51% | 50% | 49% | 2 pts |
| b3_touch_5m | all | 1114 | -0.001% | -0.010% | -0.029% | -0.076% | +0.268% | -0.279% | 49% | 47% | 48% | 48% | 4 pts |
|  | long | 565 | +0.003% | -0.003% | -0.035% | -0.057% | +0.266% | -0.275% | 51% | 50% | 51% | 50% | 6 pts |
|  | control taken long | 1114 | +0.006% | +0.016% | +0.019% | +0.048% | - | - | 51% | 53% | 52% | 52% | 4 pts |
|  | short | 549 | -0.006% | -0.016% | -0.022% | -0.095% | +0.270% | -0.283% | 48% | 44% | 46% | 46% | 6 pts |
|  | control taken short | 1114 | -0.006% | -0.016% | -0.019% | -0.048% | - | - | 49% | 47% | 48% | 47% | 4 pts |
|  | control (random side) | 1114 | +0.010% | +0.012% | +0.009% | -0.005% | +0.231% | -0.220% | 51% | 53% | 52% | 49% | 3 pts |
| b3_reentry_1m | all | 1134 | +0.002% | -0.006% | -0.036% | -0.054% | +0.246% | -0.248% | 47% | 48% | 47% | 47% | 3 pts |
|  | long | 570 | +0.004% | +0.009% | -0.011% | -0.015% | +0.247% | -0.243% | 49% | 50% | 48% | 49% | 5 pts |
|  | control taken long | 1134 | +0.005% | +0.012% | +0.027% | +0.059% | - | - | 49% | 51% | 52% | 52% | 4 pts |
|  | short | 564 | +0.001% | -0.021% | -0.061% | -0.092% | +0.245% | -0.252% | 45% | 45% | 46% | 45% | 5 pts |
|  | control taken short | 1134 | -0.005% | -0.012% | -0.027% | -0.059% | - | - | 50% | 48% | 48% | 48% | 4 pts |
|  | control (random side) | 1134 | -0.000% | +0.001% | +0.016% | +0.028% | +0.236% | -0.234% | 50% | 49% | 51% | 51% | 3 pts |

### SPY every day

| Rule | Group | Count | Avg 5m | Avg 10m | Avg 30m | Avg 60m | Best 10m | Worst 10m | In favour 5m | In favour 10m | In favour 30m | In favour 60m | Noise (±, by day) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| e1_trend | all | 2014 | -0.006% | -0.003% | -0.004% | +0.005% | +0.083% | -0.091% | 48% | 48% | 50% | 52% | 2 pts |
|  | long | 1052 | -0.005% | -0.001% | +0.005% | +0.018% | +0.080% | -0.087% | 50% | 51% | 55% | 56% | 4 pts |
|  | control taken long | 2014 | +0.001% | +0.002% | +0.009% | +0.015% | - | - | 51% | 51% | 53% | 54% | 4 pts |
|  | short | 962 | -0.007% | -0.007% | -0.013% | -0.011% | +0.087% | -0.094% | 46% | 45% | 45% | 48% | 4 pts |
|  | control taken short | 2014 | -0.001% | -0.002% | -0.009% | -0.015% | - | - | 49% | 48% | 46% | 46% | 3 pts |
|  | control (random side) | 2014 | +0.002% | +0.001% | +0.002% | +0.003% | +0.089% | -0.087% | 49% | 49% | 51% | 51% | 2 pts |
| e1_reject | all | 3577 | -0.002% | +0.001% | +0.000% | +0.007% | +0.085% | -0.088% | 50% | 51% | 51% | 53% | 2 pts |
|  | long | 1962 | -0.002% | +0.002% | +0.006% | +0.019% | +0.077% | -0.082% | 51% | 53% | 55% | 57% | 4 pts |
|  | control taken long | 3577 | +0.001% | +0.003% | +0.007% | +0.007% | - | - | 51% | 52% | 54% | 53% | 3 pts |
|  | short | 1615 | -0.003% | -0.001% | -0.006% | -0.007% | +0.095% | -0.094% | 49% | 48% | 47% | 49% | 4 pts |
|  | control taken short | 3577 | -0.001% | -0.003% | -0.007% | -0.007% | - | - | 49% | 47% | 46% | 47% | 3 pts |
|  | control (random side) | 3577 | +0.002% | +0.003% | +0.002% | +0.005% | +0.087% | -0.085% | 50% | 51% | 51% | 51% | 2 pts |
| r2_rsi_1m | all | 531 | -0.003% | -0.004% | +0.003% | +0.007% | +0.098% | -0.099% | 48% | 47% | 49% | 49% | 5 pts |
|  | long | 334 | -0.003% | -0.006% | +0.001% | +0.010% | +0.107% | -0.113% | 49% | 48% | 49% | 52% | 7 pts |
|  | control taken long | 531 | +0.005% | +0.001% | -0.009% | -0.005% | - | - | 53% | 53% | 53% | 51% | 5 pts |
|  | short | 197 | -0.002% | -0.000% | +0.008% | +0.003% | +0.083% | -0.077% | 46% | 47% | 49% | 45% | 8 pts |
|  | control taken short | 531 | -0.005% | -0.001% | +0.009% | +0.005% | - | - | 46% | 46% | 47% | 49% | 5 pts |
|  | control (random side) | 531 | +0.003% | +0.001% | +0.010% | +0.025% | +0.090% | -0.088% | 52% | 50% | 52% | 50% | 4 pts |
| r2_rsi_5m | all | 261 | -0.007% | -0.003% | -0.003% | -0.004% | +0.098% | -0.104% | 49% | 44% | 44% | 44% | 7 pts |
|  | long | 166 | -0.013% | -0.011% | -0.009% | +0.001% | +0.096% | -0.115% | 48% | 42% | 45% | 46% | 8 pts |
|  | control taken long | 261 | -0.007% | -0.001% | -0.007% | -0.001% | - | - | 51% | 52% | 50% | 51% | 7 pts |
|  | short | 95 | +0.003% | +0.011% | +0.008% | -0.012% | +0.100% | -0.086% | 51% | 48% | 43% | 42% | 11 pts |
|  | control taken short | 261 | +0.007% | +0.001% | +0.007% | +0.001% | - | - | 48% | 48% | 49% | 49% | 7 pts |
|  | control (random side) | 261 | -0.001% | +0.000% | -0.011% | -0.009% | +0.090% | -0.095% | 49% | 52% | 49% | 49% | 6 pts |
| r2_rsi_1m_sym | all | 397 | +0.003% | +0.002% | +0.007% | +0.007% | +0.098% | -0.089% | 48% | 48% | 49% | 48% | 5 pts |
|  | long | 200 | +0.008% | +0.003% | +0.006% | +0.011% | +0.112% | -0.101% | 50% | 50% | 48% | 50% | 7 pts |
|  | control taken long | 397 | +0.002% | +0.007% | +0.007% | +0.007% | - | - | 53% | 53% | 55% | 55% | 6 pts |
|  | short | 197 | -0.002% | -0.000% | +0.008% | +0.003% | +0.083% | -0.077% | 46% | 47% | 49% | 45% | 8 pts |
|  | control taken short | 397 | -0.002% | -0.007% | -0.007% | -0.007% | - | - | 46% | 46% | 45% | 45% | 6 pts |
|  | control (random side) | 397 | -0.001% | -0.002% | +0.000% | +0.010% | +0.089% | -0.091% | 49% | 47% | 49% | 52% | 5 pts |
| b3_touch_1m | all | 3948 | -0.000% | -0.002% | -0.000% | -0.004% | +0.085% | -0.085% | 49% | 49% | 49% | 48% | 2 pts |
|  | long | 1861 | +0.000% | -0.001% | +0.007% | +0.010% | +0.089% | -0.092% | 50% | 52% | 53% | 53% | 4 pts |
|  | control taken long | 3948 | +0.003% | +0.003% | +0.008% | +0.022% | - | - | 51% | 52% | 53% | 56% | 3 pts |
|  | short | 2087 | -0.001% | -0.002% | -0.007% | -0.017% | +0.081% | -0.078% | 48% | 47% | 45% | 43% | 4 pts |
|  | control taken short | 3948 | -0.003% | -0.003% | -0.008% | -0.022% | - | - | 48% | 48% | 47% | 44% | 3 pts |
|  | control (random side) | 3948 | -0.002% | -0.001% | -0.001% | -0.002% | +0.084% | -0.086% | 49% | 50% | 49% | 50% | 2 pts |
| b3_touch_5m | all | 1454 | +0.001% | -0.000% | -0.004% | -0.004% | +0.091% | -0.087% | 50% | 50% | 48% | 47% | 3 pts |
|  | long | 659 | +0.004% | +0.003% | +0.005% | +0.014% | +0.101% | -0.095% | 52% | 52% | 52% | 51% | 5 pts |
|  | control taken long | 1454 | +0.002% | +0.005% | +0.007% | +0.002% | - | - | 52% | 54% | 54% | 54% | 4 pts |
|  | short | 795 | -0.001% | -0.003% | -0.012% | -0.018% | +0.083% | -0.080% | 48% | 49% | 44% | 43% | 5 pts |
|  | control taken short | 1454 | -0.002% | -0.005% | -0.007% | -0.002% | - | - | 47% | 46% | 46% | 46% | 4 pts |
|  | control (random side) | 1454 | +0.003% | +0.000% | +0.000% | +0.002% | +0.084% | -0.084% | 50% | 50% | 51% | 51% | 3 pts |
| b3_reentry_1m | all | 1163 | -0.001% | -0.004% | -0.004% | -0.012% | +0.087% | -0.088% | 47% | 48% | 48% | 46% | 3 pts |
|  | long | 592 | +0.003% | +0.000% | +0.012% | +0.015% | +0.096% | -0.094% | 50% | 50% | 53% | 52% | 4 pts |
|  | control taken long | 1163 | +0.004% | +0.009% | +0.012% | +0.020% | - | - | 53% | 54% | 57% | 56% | 4 pts |
|  | short | 571 | -0.005% | -0.009% | -0.019% | -0.041% | +0.078% | -0.081% | 44% | 46% | 42% | 40% | 4 pts |
|  | control taken short | 1163 | -0.004% | -0.009% | -0.012% | -0.020% | - | - | 47% | 45% | 43% | 44% | 4 pts |
|  | control (random side) | 1163 | +0.002% | +0.005% | +0.004% | +0.003% | +0.087% | -0.083% | 50% | 50% | 51% | 50% | 3 pts |


## e1 races: stop vs 1.5×, 2× the risk and the 20-bar swing (within 60 minutes)

### ATR pick

| Rule | Side | Target | Signals | Target first | Stop first | Same bar | Neither | Control: target first | Control: stop first | Avg risk |
|---|---|---|---|---|---|---|---|---|---|---|
| e1_trend | long | 1.5× risk | 983 | 354 (36%) | 525 (53%) | 0 (0%) | 104 (11%) | 332 (34%) | 518 (53%) | 0.30% |
| e1_trend | long | 2× risk | 983 | 268 (27%) | 564 (57%) | 0 (0%) | 151 (15%) | 237 (24%) | 563 (57%) | 0.30% |
| e1_trend | long | 20-bar swing (95 already past) | 888 | 569 (64%) | 309 (35%) | 1 (0%) | 9 (1%) | 554 (62%) | 311 (35%) | 0.30% |
| e1_trend | short | 1.5× risk | 957 | 354 (37%) | 514 (54%) | 0 (0%) | 89 (9%) | 303 (32%) | 515 (54%) | 0.30% |
| e1_trend | short | 2× risk | 957 | 267 (28%) | 548 (57%) | 0 (0%) | 142 (15%) | 223 (23%) | 546 (57%) | 0.30% |
| e1_trend | short | 20-bar swing (98 already past) | 859 | 543 (63%) | 306 (36%) | 1 (0%) | 9 (1%) | 526 (61%) | 306 (36%) | 0.30% |
| e1_reject | long | 1.5× risk | 1704 | 632 (37%) | 932 (55%) | 0 (0%) | 140 (8%) | 630 (37%) | 870 (51%) | 0.27% |
| e1_reject | long | 2× risk | 1704 | 484 (28%) | 996 (58%) | 0 (0%) | 224 (13%) | 497 (29%) | 930 (55%) | 0.27% |
| e1_reject | long | 20-bar swing (277 already past) | 1427 | 957 (67%) | 460 (32%) | 2 (0%) | 8 (1%) | 954 (67%) | 429 (30%) | 0.27% |
| e1_reject | short | 1.5× risk | 1552 | 576 (37%) | 853 (55%) | 1 (0%) | 122 (8%) | 514 (33%) | 868 (56%) | 0.29% |
| e1_reject | short | 2× risk | 1552 | 438 (28%) | 915 (59%) | 0 (0%) | 199 (13%) | 385 (25%) | 928 (60%) | 0.29% |
| e1_reject | short | 20-bar swing (226 already past) | 1326 | 877 (66%) | 442 (33%) | 2 (0%) | 5 (0%) | 862 (65%) | 434 (33%) | 0.29% |

### SPY every day

| Rule | Side | Target | Signals | Target first | Stop first | Same bar | Neither | Control: target first | Control: stop first | Avg risk |
|---|---|---|---|---|---|---|---|---|---|---|
| e1_trend | long | 1.5× risk | 1052 | 370 (35%) | 574 (55%) | 0 (0%) | 108 (10%) | 345 (33%) | 575 (55%) | 0.12% |
| e1_trend | long | 2× risk | 1052 | 269 (26%) | 615 (58%) | 0 (0%) | 168 (16%) | 247 (23%) | 605 (58%) | 0.12% |
| e1_trend | long | 20-bar swing (123 already past) | 929 | 603 (65%) | 319 (34%) | 1 (0%) | 6 (1%) | 577 (62%) | 335 (36%) | 0.12% |
| e1_trend | short | 1.5× risk | 962 | 329 (34%) | 568 (59%) | 1 (0%) | 64 (7%) | 354 (37%) | 513 (53%) | 0.12% |
| e1_trend | short | 2× risk | 962 | 244 (25%) | 614 (64%) | 1 (0%) | 103 (11%) | 269 (28%) | 547 (57%) | 0.12% |
| e1_trend | short | 20-bar swing (112 already past) | 850 | 493 (58%) | 348 (41%) | 1 (0%) | 8 (1%) | 543 (64%) | 294 (35%) | 0.12% |
| e1_reject | long | 1.5× risk | 1962 | 698 (36%) | 1032 (53%) | 1 (0%) | 231 (12%) | 668 (34%) | 1050 (54%) | 0.12% |
| e1_reject | long | 2× risk | 1962 | 503 (26%) | 1104 (56%) | 0 (0%) | 355 (18%) | 489 (25%) | 1120 (57%) | 0.12% |
| e1_reject | long | 20-bar swing (420 already past) | 1542 | 1071 (69%) | 456 (30%) | 3 (0%) | 12 (1%) | 1078 (70%) | 431 (28%) | 0.12% |
| e1_reject | short | 1.5× risk | 1615 | 570 (35%) | 925 (57%) | 2 (0%) | 118 (7%) | 551 (34%) | 879 (54%) | 0.12% |
| e1_reject | short | 2× risk | 1615 | 442 (27%) | 982 (61%) | 2 (0%) | 189 (12%) | 415 (26%) | 935 (58%) | 0.12% |
| e1_reject | short | 20-bar swing (327 already past) | 1288 | 837 (65%) | 440 (34%) | 3 (0%) | 8 (1%) | 877 (68%) | 392 (30%) | 0.12% |


## b3 races: reaching the opposite band (within 60 minutes)

### ATR pick

| Rule | Side | Signals | Avg distance to band | Reached within 60 min | Median minutes | Control: reached | Control: median minutes |
|---|---|---|---|---|---|---|---|
| b3_touch_1m | long | 1560 | 0.52% | 710 (46%) | 16 | 729 (47%) | 15 |
| b3_touch_1m | short | 1623 | 0.50% | 697 (43%) | 16 | 760 (47%) | 15 |
| b3_touch_5m | long | 565 | 1.47% | 88 (16%) | 23 | 80 (14%) | 28 |
| b3_touch_5m | short | 549 | 1.57% | 88 (16%) | 22 | 47 (9%) | 24 |
| b3_reentry_1m | long | 570 | 0.72% | 199 (35%) | 19 | 196 (34%) | 18 |
| b3_reentry_1m | short | 564 | 0.74% | 198 (35%) | 22 | 210 (37%) | 16 |

### SPY every day

| Rule | Side | Signals | Avg distance to band | Reached within 60 min | Median minutes | Control: reached | Control: median minutes |
|---|---|---|---|---|---|---|---|
| b3_touch_1m | long | 1861 | 0.19% | 884 (48%) | 16 | 870 (47%) | 15 |
| b3_touch_1m | short | 2087 | 0.19% | 894 (43%) | 18 | 1004 (48%) | 17 |
| b3_touch_5m | long | 659 | 0.54% | 103 (16%) | 28 | 86 (13%) | 28 |
| b3_touch_5m | short | 795 | 0.51% | 115 (14%) | 25 | 112 (14%) | 29 |
| b3_reentry_1m | long | 592 | 0.27% | 226 (38%) | 18 | 238 (40%) | 16 |
| b3_reentry_1m | short | 571 | 0.24% | 192 (34%) | 21 | 239 (42%) | 20 |


---

Full per-trade tables: [history/2026-10-28-ed-rules-v1.md](history/2026-10-28-ed-rules-v1.md)
