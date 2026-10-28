# Squeeze test series (TTM release), October 28

Squeeze test series, October 28. The signal test is the gate. The default rulebook.yaml is unchanged; every variant is a file in variants/.

## Findings

- **No squeeze rule passes the gate.** On the ATR pick and on SPY, none of the five rules moves the stock our way clearly more often than random entries do. That covers the current squeeze rule (s1) and the TTM release with N = 5, 10 and 15 on 1-minute bars (s2–s4) and N = 5 on 5-minute bars (s5).
  - The best-looking row is s4 on the ATR pick: 62% in favour at +5 minutes with 65 signals. The noise band there is ±12 points.
  - The same rule on SPY is 48% at +5 minutes and 57% at +10.
  - Across about 50 rows a few will look this good by chance, and nothing holds on both pick methods and at several horizons.
- **Claim (a), "longer squeezes produce bigger moves": not supported.** Move size doesn't grow with squeeze length, for 1-minute or 5-minute squeezes, on either pick method.
  - The rank correlations are between −0.07 and +0.08, all inside the noise.
  - On 1-minute bars, releases move no more than random bars do.
- **Claim (b), "2× the squeeze width our way before 1× against": rare, and no more often than chance.**
  - On 1-minute bars the stock reached 2× our way first after 15–19% of releases. It reached 1× against first after 40–55%.
  - Random entries with the same width and a random direction did about the same: 9–20% and 40–55%. In a random walk with no drift, about a third of the races that finish would end at the 2× target.
  - On 5-minute bars it was 27% (ATR pick) and 18% (SPY), against 25% and 21% for the control.
- **The one thing that stands out is size, not direction.**
  - On the ATR pick, the stock moved more after 5-minute releases (s5) than after random bars on the same days and names: on average 0.66% vs 0.41% at +30 minutes (about 3 standard errors) and 0.80% vs 0.53% at +60.
  - The direction from TTM momentum was still a coin flip (47–57% in favour).
  - 40 of the 53 releases were on TSLA. On SPY the difference is small and within noise (0.15% vs 0.12% at +30 minutes).
  - This could be a volatility signal rather than a direction signal. It would need its own test before anyone relies on it.

## Method

- **Signal test:** same as October 27 and 28, with +60 minutes added.
  - Every signal whose bar closes inside the entry window (9:35 to 11:50) counts. Repeats of the same setup and side within 5 minutes are skipped.
  - Moves are in the signal's direction, in percent of the signal bar's close. Best and worst are within 10 minutes.
  - The control group has one random entry per signal (squeeze or pullback), on the same day and name, in the same window, with a random direction (seed 7). So each run has its own control draw.
  - **Noise** is two standard errors of the in-favour share (100/√count points).
  - s1 reproduces the October 27 signals exactly.
- **TTM squeeze momentum** (LazyBear's formula): the 20-bar linear-regression value of close − average(midpoint of the 20-bar highest high and lowest low, 20-bar simple moving average of close).
- **Squeeze release:** the first bar where the Bollinger Bands (20, 2) are back outside the Keltner Channel (20, 1.5 × ATR 20), after at least N bars inside. It is long if momentum is above 0 and rising, short if below 0 and falling. There is no volume check.
- **5-minute bars (s5):** bars are built from the 1-minute bars on clock boundaries (9:30, 9:35, …). Each 5-minute bar is decided at its close, on its last minute.
  - s5 keeps 300 minutes of the previous session for warm-up instead of 90, so the 5-minute indicators are ready at the open.
- **Pullback signals are the same rules in every run, but their counts differ.** A bar gives only one signal and the squeeze rule is checked first, so a different squeeze rule frees or takes different bars.
- **Claim (a):** this uses every release after a squeeze of at least 5 bars (s2 for 1-minute, s5 for 5-minute), whether or not momentum gives a direction.
  - **Size** is the absolute move at each horizon. **Range** is the highest high minus the lowest low over the next 30 or 60 minutes. **Width** is the squeeze's highest high minus lowest low. All are in percent of the release bar's close.
  - "Random bars" are that run's control group, measured the same way.
- **Claim (b):** this uses every release with a momentum direction, within 60 minutes. "Same bar" means one 1-minute bar reached both levels.
  - The control race uses a random bar in the window on the same day, a random direction and the same width.
  - s3 and s4 are subsets of s2 (longer squeezes only).

## Signal test (the gate), 2026-01-02 to 2026-10-23

### ATR pick

| Group | Run | Count | Avg 5m | Avg 10m | Avg 30m | Avg 60m | Best 10m | Worst 10m | In favour 5m | In favour 10m | In favour 30m | In favour 60m | Noise (±) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze (all) | s1 current squeeze rule | 69 | -0.011% | -0.001% | +0.066% | +0.072% | +0.235% | -0.239% | 54% | 51% | 55% | 55% | 12 pts |
| squeeze (all) | s2 TTM release, 1 min, N=5 | 262 | +0.003% | -0.002% | +0.017% | +0.020% | +0.201% | -0.202% | 52% | 51% | 52% | 51% | 6 pts |
| squeeze (all) | s3 TTM release, 1 min, N=10 | 128 | +0.008% | +0.006% | +0.050% | +0.027% | +0.204% | -0.199% | 56% | 55% | 59% | 55% | 9 pts |
| squeeze (all) | s4 TTM release, 1 min, N=15 | 65 | +0.019% | +0.031% | +0.085% | +0.051% | +0.192% | -0.155% | 62% | 57% | 60% | 52% | 12 pts |
| squeeze (all) | s5 TTM release, 5 min, N=5 | 51 | -0.036% | -0.053% | -0.041% | +0.095% | +0.450% | -0.496% | 49% | 47% | 55% | 57% | 14 pts |
| squeeze long | s1 current squeeze rule | 39 | +0.004% | +0.029% | +0.117% | +0.128% | +0.250% | -0.225% | 59% | 54% | 54% | 56% | 16 pts |
| squeeze long | s2 TTM release, 1 min, N=5 | 150 | -0.003% | +0.001% | +0.040% | +0.058% | +0.188% | -0.201% | 47% | 51% | 54% | 55% | 8 pts |
| squeeze long | s3 TTM release, 1 min, N=10 | 76 | +0.006% | +0.016% | +0.038% | +0.036% | +0.193% | -0.195% | 50% | 57% | 62% | 58% | 11 pts |
| squeeze long | s4 TTM release, 1 min, N=15 | 40 | +0.008% | +0.032% | +0.101% | +0.070% | +0.178% | -0.150% | 57% | 57% | 62% | 57% | 16 pts |
| squeeze long | s5 TTM release, 5 min, N=5 | 25 | -0.096% | -0.020% | -0.050% | -0.047% | +0.461% | -0.569% | 48% | 52% | 52% | 48% | 20 pts |
| squeeze short | s1 current squeeze rule | 30 | -0.031% | -0.041% | -0.002% | -0.001% | +0.214% | -0.257% | 47% | 47% | 57% | 53% | 18 pts |
| squeeze short | s2 TTM release, 1 min, N=5 | 112 | +0.010% | -0.007% | -0.014% | -0.030% | +0.219% | -0.204% | 57% | 52% | 50% | 46% | 9 pts |
| squeeze short | s3 TTM release, 1 min, N=10 | 52 | +0.012% | -0.009% | +0.067% | +0.013% | +0.221% | -0.205% | 65% | 54% | 56% | 50% | 14 pts |
| squeeze short | s4 TTM release, 1 min, N=15 | 25 | +0.036% | +0.029% | +0.058% | +0.020% | +0.213% | -0.162% | 68% | 56% | 56% | 44% | 20 pts |
| squeeze short | s5 TTM release, 5 min, N=5 | 26 | +0.022% | -0.084% | -0.033% | +0.232% | +0.440% | -0.426% | 50% | 42% | 58% | 65% | 20 pts |
| control (random) | s1 current squeeze rule | 133 | +0.027% | +0.032% | -0.001% | +0.029% | +0.244% | -0.218% | 50% | 45% | 43% | 46% | 9 pts |
| control (random) | s2 TTM release, 1 min, N=5 | 337 | +0.006% | +0.005% | +0.016% | +0.011% | +0.229% | -0.220% | 53% | 54% | 52% | 52% | 5 pts |
| control (random) | s3 TTM release, 1 min, N=10 | 206 | -0.008% | -0.011% | +0.000% | -0.010% | +0.222% | -0.244% | 51% | 50% | 50% | 49% | 7 pts |
| control (random) | s4 TTM release, 1 min, N=15 | 143 | -0.012% | -0.030% | -0.031% | -0.026% | +0.211% | -0.226% | 43% | 45% | 48% | 47% | 8 pts |
| control (random) | s5 TTM release, 5 min, N=5 | 129 | -0.032% | -0.042% | -0.033% | -0.024% | +0.241% | -0.278% | 47% | 46% | 48% | 46% | 9 pts |
| pullback (all) | s1 current squeeze rule | 64 | -0.010% | -0.005% | -0.008% | +0.003% | +0.213% | -0.222% | 50% | 48% | 52% | 45% | 12 pts |
| pullback (all) | s2 TTM release, 1 min, N=5 | 75 | -0.018% | -0.033% | -0.033% | -0.037% | +0.214% | -0.247% | 48% | 45% | 49% | 45% | 12 pts |
| pullback (all) | s3 TTM release, 1 min, N=10 | 78 | -0.018% | -0.035% | -0.038% | -0.044% | +0.213% | -0.247% | 47% | 45% | 49% | 44% | 11 pts |
| pullback (all) | s4 TTM release, 1 min, N=15 | 78 | -0.018% | -0.035% | -0.038% | -0.044% | +0.213% | -0.247% | 47% | 45% | 49% | 44% | 11 pts |
| pullback (all) | s5 TTM release, 5 min, N=5 | 78 | -0.018% | -0.035% | -0.038% | -0.044% | +0.213% | -0.247% | 47% | 45% | 49% | 44% | 11 pts |

### SPY every day

| Group | Run | Count | Avg 5m | Avg 10m | Avg 30m | Avg 60m | Best 10m | Worst 10m | In favour 5m | In favour 10m | In favour 30m | In favour 60m | Noise (±) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze (all) | s1 current squeeze rule | 50 | -0.021% | -0.001% | -0.024% | -0.019% | +0.088% | -0.103% | 46% | 54% | 46% | 46% | 14 pts |
| squeeze (all) | s2 TTM release, 1 min, N=5 | 226 | -0.000% | +0.003% | -0.018% | -0.010% | +0.082% | -0.084% | 50% | 55% | 47% | 55% | 7 pts |
| squeeze (all) | s3 TTM release, 1 min, N=10 | 92 | +0.001% | +0.020% | -0.006% | -0.013% | +0.082% | -0.074% | 51% | 62% | 49% | 55% | 10 pts |
| squeeze (all) | s4 TTM release, 1 min, N=15 | 44 | -0.006% | +0.016% | -0.025% | -0.032% | +0.077% | -0.078% | 48% | 57% | 50% | 52% | 15 pts |
| squeeze (all) | s5 TTM release, 5 min, N=5 | 38 | +0.006% | +0.011% | -0.030% | +0.031% | +0.092% | -0.081% | 58% | 47% | 47% | 58% | 16 pts |
| squeeze long | s1 current squeeze rule | 25 | -0.010% | +0.015% | -0.018% | -0.036% | +0.084% | -0.090% | 52% | 64% | 48% | 40% | 20 pts |
| squeeze long | s2 TTM release, 1 min, N=5 | 118 | +0.008% | +0.008% | -0.001% | +0.011% | +0.073% | -0.075% | 47% | 55% | 49% | 62% | 9 pts |
| squeeze long | s3 TTM release, 1 min, N=10 | 52 | +0.010% | +0.018% | +0.030% | +0.028% | +0.070% | -0.066% | 52% | 65% | 56% | 65% | 14 pts |
| squeeze long | s4 TTM release, 1 min, N=15 | 22 | +0.015% | +0.025% | +0.032% | +0.012% | +0.070% | -0.049% | 55% | 68% | 55% | 59% | 21 pts |
| squeeze long | s5 TTM release, 5 min, N=5 | 20 | -0.010% | -0.026% | -0.074% | -0.026% | +0.064% | -0.088% | 50% | 40% | 35% | 45% | 22 pts |
| squeeze short | s1 current squeeze rule | 25 | -0.032% | -0.018% | -0.030% | -0.003% | +0.093% | -0.116% | 40% | 44% | 44% | 52% | 20 pts |
| squeeze short | s2 TTM release, 1 min, N=5 | 108 | -0.009% | -0.003% | -0.037% | -0.032% | +0.091% | -0.094% | 53% | 56% | 44% | 47% | 10 pts |
| squeeze short | s3 TTM release, 1 min, N=10 | 40 | -0.010% | +0.022% | -0.052% | -0.067% | +0.098% | -0.083% | 50% | 57% | 40% | 42% | 16 pts |
| squeeze short | s4 TTM release, 1 min, N=15 | 22 | -0.027% | +0.008% | -0.081% | -0.076% | +0.085% | -0.108% | 41% | 45% | 45% | 45% | 21 pts |
| squeeze short | s5 TTM release, 5 min, N=5 | 18 | +0.024% | +0.052% | +0.019% | +0.094% | +0.122% | -0.074% | 67% | 56% | 61% | 72% | 24 pts |
| control (random) | s1 current squeeze rule | 123 | -0.001% | -0.007% | -0.008% | -0.008% | +0.088% | -0.092% | 52% | 51% | 55% | 52% | 9 pts |
| control (random) | s2 TTM release, 1 min, N=5 | 301 | -0.003% | -0.013% | -0.008% | -0.000% | +0.077% | -0.091% | 48% | 46% | 51% | 53% | 6 pts |
| control (random) | s3 TTM release, 1 min, N=10 | 167 | +0.001% | -0.008% | +0.009% | +0.023% | +0.087% | -0.086% | 48% | 47% | 57% | 51% | 8 pts |
| control (random) | s4 TTM release, 1 min, N=15 | 120 | +0.003% | +0.001% | -0.006% | +0.002% | +0.083% | -0.081% | 48% | 52% | 48% | 48% | 9 pts |
| control (random) | s5 TTM release, 5 min, N=5 | 115 | +0.001% | -0.004% | +0.007% | +0.006% | +0.081% | -0.083% | 57% | 53% | 50% | 50% | 9 pts |
| pullback (all) | s1 current squeeze rule | 73 | -0.003% | -0.014% | -0.022% | -0.036% | +0.076% | -0.094% | 47% | 47% | 52% | 41% | 12 pts |
| pullback (all) | s2 TTM release, 1 min, N=5 | 75 | -0.003% | -0.013% | -0.019% | -0.036% | +0.077% | -0.094% | 47% | 48% | 53% | 41% | 12 pts |
| pullback (all) | s3 TTM release, 1 min, N=10 | 75 | -0.003% | -0.013% | -0.019% | -0.036% | +0.077% | -0.094% | 47% | 48% | 53% | 41% | 12 pts |
| pullback (all) | s4 TTM release, 1 min, N=15 | 76 | -0.003% | -0.013% | -0.020% | -0.036% | +0.076% | -0.093% | 46% | 47% | 53% | 41% | 11 pts |
| pullback (all) | s5 TTM release, 5 min, N=5 | 77 | -0.003% | -0.013% | -0.019% | -0.036% | +0.075% | -0.093% | 45% | 48% | 53% | 40% | 11 pts |


## Claim (a): do longer squeezes produce bigger moves?

### ATR pick, 1-minute squeezes (s2 releases, every squeeze of 5 bars or more)

| Squeeze length | Releases | Avg width | Avg size 5m | Avg size 10m | Avg size 30m | Avg size 60m | Avg range 30m | Avg range 60m |
|---|---|---|---|---|---|---|---|---|
| 5–9 bars | 143 | 0.358% | 0.150% | 0.207% | 0.369% | 0.466% | 0.715% | 0.926% |
| 10–14 bars | 63 | 0.432% | 0.144% | 0.237% | 0.399% | 0.465% | 0.750% | 0.960% |
| 15–19 bars | 34 | 0.388% | 0.103% | 0.140% | 0.290% | 0.438% | 0.617% | 0.853% |
| 20–29 bars | 26 | 0.414% | 0.113% | 0.156% | 0.332% | 0.545% | 0.708% | 1.059% |
| 30+ bars | 6 | 0.495% | 0.158% | 0.130% | 0.188% | 0.291% | 0.692% | 0.832% |
| all releases | 272 | 0.387% | 0.140% | 0.199% | 0.358% | 0.466% | 0.710% | 0.935% |
| random bars (this run's control group) | 337 | - | 0.163% | 0.218% | 0.376% | 0.478% | - | - |

Rank correlation between squeeze length and move size: -0.07 at +30 minutes, -0.00 at +60 minutes (0 = no relation, +1 = longer always bigger; with 272 releases, about ±0.12 is noise).

### ATR pick, 5-minute squeezes (s5 releases, every squeeze of 5 five-minute bars or more)

| Squeeze length | Releases | Avg width | Avg size 5m | Avg size 10m | Avg size 30m | Avg size 60m | Avg range 30m | Avg range 60m |
|---|---|---|---|---|---|---|---|---|
| 5–7 bars | 12 | 0.520% | 0.229% | 0.370% | 0.585% | 0.512% | 1.131% | 1.311% |
| 8–11 bars | 5 | 0.220% | 0.407% | 0.691% | 0.908% | 0.971% | 1.446% | 1.872% |
| 12+ bars | 36 | 0.569% | 0.407% | 0.513% | 0.651% | 0.864% | 1.406% | 1.669% |
| all releases | 53 | 0.525% | 0.367% | 0.497% | 0.660% | 0.795% | 1.347% | 1.607% |
| random bars (this run's control group) | 129 | - | 0.193% | 0.265% | 0.408% | 0.532% | - | - |

Rank correlation between squeeze length and move size: +0.05 at +30 minutes, +0.08 at +60 minutes (0 = no relation, +1 = longer always bigger; with 53 releases, about ±0.27 is noise).

### SPY every day, 1-minute squeezes (s2 releases, every squeeze of 5 bars or more)

| Squeeze length | Releases | Avg width | Avg size 5m | Avg size 10m | Avg size 30m | Avg size 60m | Avg range 30m | Avg range 60m |
|---|---|---|---|---|---|---|---|---|
| 5–9 bars | 139 | 0.127% | 0.067% | 0.089% | 0.137% | 0.188% | 0.289% | 0.377% |
| 10–14 bars | 49 | 0.152% | 0.045% | 0.056% | 0.118% | 0.178% | 0.272% | 0.369% |
| 15–19 bars | 29 | 0.150% | 0.050% | 0.064% | 0.151% | 0.187% | 0.271% | 0.348% |
| 20–29 bars | 11 | 0.144% | 0.054% | 0.056% | 0.134% | 0.182% | 0.262% | 0.318% |
| 30+ bars | 5 | 0.197% | 0.075% | 0.157% | 0.102% | 0.144% | 0.320% | 0.348% |
| all releases | 233 | 0.137% | 0.060% | 0.079% | 0.134% | 0.185% | 0.282% | 0.368% |
| random bars (this run's control group) | 301 | - | 0.061% | 0.080% | 0.143% | 0.206% | - | - |

Rank correlation between squeeze length and move size: +0.02 at +30 minutes, -0.01 at +60 minutes (0 = no relation, +1 = longer always bigger; with 233 releases, about ±0.13 is noise).

### SPY every day, 5-minute squeezes (s5 releases, every squeeze of 5 five-minute bars or more)

| Squeeze length | Releases | Avg width | Avg size 5m | Avg size 10m | Avg size 30m | Avg size 60m | Avg range 30m | Avg range 60m |
|---|---|---|---|---|---|---|---|---|
| 5–7 bars | 16 | 0.185% | 0.060% | 0.076% | 0.139% | 0.200% | 0.300% | 0.421% |
| 8–11 bars | 9 | 0.243% | 0.052% | 0.072% | 0.162% | 0.217% | 0.282% | 0.377% |
| 12+ bars | 14 | 0.181% | 0.068% | 0.089% | 0.141% | 0.201% | 0.326% | 0.471% |
| all releases | 39 | 0.197% | 0.061% | 0.080% | 0.145% | 0.204% | 0.305% | 0.429% |
| random bars (this run's control group) | 115 | - | 0.061% | 0.080% | 0.124% | 0.169% | - | - |

Rank correlation between squeeze length and move size: -0.07 at +30 minutes, -0.01 at +60 minutes (0 = no relation, +1 = longer always bigger; with 39 releases, about ±0.32 is noise).


## Claim (b): 2× the squeeze width our way before 1× against?

### ATR pick

| Run | Releases with a direction | 2× our way first | 1× against first | Same bar | Neither in 60 min | Control: 2× first | Control: 1× against first |
|---|---|---|---|---|---|---|---|
| s2 TTM release, 1 min, N=5 | 262 | 46 (18%) | 132 (50%) | 0 (0%) | 84 (32%) | 52 (20%) | 126 (48%) |
| s3 TTM release, 1 min, N=10 | 128 | 20 (16%) | 57 (45%) | 0 (0%) | 51 (40%) | 16 (12%) | 65 (51%) |
| s4 TTM release, 1 min, N=15 | 65 | 11 (17%) | 26 (40%) | 0 (0%) | 28 (43%) | 6 (9%) | 30 (46%) |
| s5 TTM release, 5 min, N=5 | 51 | 14 (27%) | 22 (43%) | 2 (4%) | 13 (25%) | 13 (25%) | 19 (37%) |

### SPY every day

| Run | Releases with a direction | 2× our way first | 1× against first | Same bar | Neither in 60 min | Control: 2× first | Control: 1× against first |
|---|---|---|---|---|---|---|---|
| s2 TTM release, 1 min, N=5 | 226 | 43 (19%) | 124 (55%) | 0 (0%) | 59 (26%) | 46 (20%) | 117 (52%) |
| s3 TTM release, 1 min, N=10 | 92 | 14 (15%) | 44 (48%) | 0 (0%) | 34 (37%) | 15 (16%) | 37 (40%) |
| s4 TTM release, 1 min, N=15 | 44 | 7 (16%) | 21 (48%) | 0 (0%) | 16 (36%) | 6 (14%) | 24 (55%) |
| s5 TTM release, 5 min, N=5 | 38 | 7 (18%) | 19 (50%) | 0 (0%) | 12 (32%) | 8 (21%) | 10 (26%) |


---

Full per-trade tables: [history/2026-10-28-squeeze-test-series.md](history/2026-10-28-squeeze-test-series.md)
