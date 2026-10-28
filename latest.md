# T10b: T10 rerun with the control on another day (2019-2023)

**Comparisons: 98 rule × side × bar-size candidates, each judged in all9 and spy (196 rows, 392 tests of the 3-standard-error bar at 10 and 30 minutes); atr_pick is shown for comparison only.** If no rule had any edge, a single test clears 3 standard errors one time in about 740, so about 0.5 of the 392 tests would clear it by chance, and a full PASS (both horizons, 4 of 5 years, both universes) would almost never happen by chance (well under 0.1 expected).

## Findings

**PASS: none.** No rule × side × bar size meets the pass bar in both all9 and spy.

**PASS: none, and nothing comes close.** With the control on another day, no rule × side × bar size meets
the pass bar in either universe, let alone both. None is options-worthy.

**The control is fixed.** After every rule, the control taken the same way now moves only by the market's
drift: between -0.02% and +0.02% at 10 minutes, for rows with at least 1,000 signals in all9. In T10, the
same-day control moved between -0.09% and +0.23% depending on the rule. The large T10 gaps are gone. b3_touch
long at 1-minute bars was +10.9 points (z +47) in T10 and is +0.3 points (z +0.8) now.

**Chance level.** Of the 392 tests of the 3-standard-error bar, one clears it (about 0.5 expected by chance):
gap1_cont short in spy at 30 minutes, with only 83 signals and z +0.7 at 10 minutes. Three tests sit at
-3.0 to -3.2 (r2_rsi and r2_rsi_sym short on 3- and 4-minute bars, all9). In rows with at least 300 signals,
the best row's smaller z of 10 and 30 minutes is +1.1 (gap0.5_cont short, all9). Shares our way are 43-59%,
gaps against the control are -9 to +9 points, and no average move at 30 minutes exceeds +0.09%.

**Conclusion, unchanged from T10's corrected reading.** The rulebook's squeeze and pullback rules, Ed's six rules,
opening-range breakouts, gap continuation and fill, and the first half hour show no direction edge in 2019-2023,
at any bar size from 1 to 5 minutes, in all9 or in spy.

**FOMC days:** 40 decision days skipped (of 1,258 sessions), dates in the method section.

**The 10 strongest results** (all9 and spy rows, ranked by the smaller of the 10- and 30-minute z):

| # | Rule | Universe | Count | Gap 10m (z) | Gap 30m (z) | Avg 30m % | Years held | Year by year: gap 30m (pts) |
|---|---|---|---|---|---|---|---|---|
| 1 | gap0.5_cont short | spy | 206 | +10.7 (+2.1) | +10.7 (+2.3) | +0.090 | 3/5 | 2019: +16.7✓, 2020: +2.2, 2021: +14.8✓, 2022: +12.9✓, 2023: +9.1 |
| 2 | gap1_cont long | spy | 70 | +11.4 (+1.4) | +12.9 (+1.5) | +0.108 | 0/5 | 2019: +0.0, 2020: +14.7, 2021: +20.0, 2022: +13.6, 2023: +0.0 |
| 3 | first_half_hour long | spy | 178 | +6.2 (+1.2) | +5.6 (+1.1) | +0.020 | 2/5 | 2019: +27.3✓, 2020: -2.3, 2021: +15.6✓, 2022: +6.9, 2023: -18.2 |
| 4 | gap0.5_cont short | all9 | 2764 | +2.2 (+1.1) | +4.9 (+2.5) | +0.047 | 1/5 | 2019: +11.1✓, 2020: +0.2, 2021: +2.0, 2022: +5.6, 2023: +5.3 |
| 5 | b3_touch long, 3m bars | all9 | 47313 | +0.7 (+1.4) | +0.7 (+1.1) | +0.002 | 3/5 | 2019: +1.2, 2020: +1.6✓, 2021: +0.9✓, 2022: -2.1, 2023: +1.9✓ |
| 6 | b3_reentry long, 2m bars | all9 | 19081 | +1.0 (+1.5) | +0.8 (+1.0) | -0.002 | 3/5 | 2019: +1.3, 2020: +2.7✓, 2021: +3.3✓, 2022: -4.0, 2023: +0.9✓ |
| 7 | squeeze long, 4m bars | all9 | 526 | +4.0 (+1.2) | +3.0 (+1.0) | +0.083 | 2/5 | 2019: +3.7✓, 2020: -1.9, 2021: +4.1✓, 2022: +8.9, 2023: +1.6 |
| 8 | b3_touch short, 3m bars | all9 | 49825 | +0.7 (+1.3) | +0.6 (+0.9) | -0.011 | 0/5 | 2019: +0.2, 2020: +1.1, 2021: +1.0, 2022: -0.2, 2023: +0.8 |
| 9 | gap1_cont short | spy | 83 | +6.0 (+0.7) | +25.3 (+3.6) | +0.111 | 2/5 | 2019: +28.6✓, 2020: +17.9, 2021: +55.6✓, 2022: +21.9, 2023: +28.6 |
| 10 | b3_touch long, 3m bars | spy | 6449 | +0.6 (+0.7) | +1.6 (+1.4) | +0.004 | 2/5 | 2019: +3.9, 2020: +3.8✓, 2021: +0.2✓, 2022: -0.5, 2023: +0.3 |

Gap = share our way minus the control taken the same way, in percentage points; ✓ = the year holds.

## Drift check: the control's own move, by rule

With the control on another day, it no longer shares the move that made the signal, so the control taken the same way should move about the same after every rule: only the market's drift over the year (up for longs in 2019-2023, so down for shorts), and the random-direction control should sit near 50%. The table shows all9 at 1-minute bars and the day rules (compare T10, where the same-day control's average move ranged from -0.09% to +0.23% depending on the rule).

| Rule (all9, 1m bars) | Count | Our way 10m | Avg 10m % | Ctrl taken same way: our way 10m | its avg 10m % | Random-direction ctrl: our way 10m | Gap vs same-way ctrl (z) | Gap vs random-direction ctrl (z) |
|---|---|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 2052 | 50.2% | +0.009 | 51.5% | +0.020 | 49.3% | -1.3 (-0.8) | +0.9 (+0.5) |
| squeeze short, 1m bars | 1873 | 48.6% | +0.019 | 48.1% | -0.010 | 49.9% | +0.5 (+0.3) | -1.3 (-0.7) |
| pullback long, 1m bars | 2888 | 50.1% | +0.007 | 50.8% | +0.008 | 49.8% | -0.7 (-0.5) | +0.3 (+0.2) |
| pullback short, 1m bars | 2347 | 47.3% | -0.005 | 47.6% | -0.006 | 48.6% | -0.3 (-0.2) | -1.3 (-0.8) |
| e1_trend long, 1m bars | 57035 | 50.1% | +0.003 | 50.0% | +0.004 | 49.1% | +0.1 (+0.2) | +1.0 (+2.4) |
| e1_trend short, 1m bars | 54931 | 48.5% | -0.002 | 48.7% | -0.003 | 49.2% | -0.2 (-0.4) | -0.7 (-1.6) |
| e1_reject long, 1m bars | 90864 | 49.6% | +0.003 | 50.1% | +0.002 | 49.4% | -0.5 (-1.4) | +0.2 (+0.6) |
| e1_reject short, 1m bars | 84770 | 48.1% | -0.001 | 48.3% | -0.006 | 49.3% | -0.2 (-0.6) | -1.2 (-3.2) |
| r2_rsi long, 1m bars | 14006 | 50.2% | -0.003 | 49.6% | +0.001 | 49.7% | +0.6 (+0.8) | +0.6 (+0.8) |
| r2_rsi short, 1m bars | 9249 | 47.5% | -0.013 | 48.9% | -0.002 | 48.4% | -1.4 (-1.7) | -1.0 (-1.1) |
| r2_rsi_sym long, 1m bars | 8065 | 51.4% | +0.000 | 50.1% | +0.000 | 50.5% | +1.3 (+1.3) | +0.9 (+0.9) |
| r2_rsi_sym short, 1m bars | 9249 | 47.5% | -0.013 | 49.1% | -0.003 | 49.3% | -1.6 (-1.9) | -1.8 (-2.1) |
| b3_touch long, 1m bars | 85790 | 50.6% | +0.006 | 50.3% | +0.004 | 49.5% | +0.3 (+0.8) | +1.2 (+3.1) |
| b3_touch short, 1m bars | 88480 | 48.4% | -0.003 | 48.5% | -0.002 | 49.3% | -0.1 (-0.2) | -0.9 (-2.3) |
| b3_reentry long, 1m bars | 33096 | 50.9% | +0.006 | 50.6% | +0.006 | 49.0% | +0.3 (+0.6) | +1.9 (+3.5) |
| b3_reentry short, 1m bars | 32355 | 48.6% | -0.005 | 48.4% | -0.003 | 49.1% | +0.2 (+0.5) | -0.5 (-0.9) |
| orb15 long, 1m bars | 2084 | 50.9% | +0.025 | 50.9% | -0.003 | 52.1% | -0.0 (-0.0) | -1.2 (-0.7) |
| orb15 short, 1m bars | 1939 | 46.4% | -0.015 | 48.8% | -0.005 | 47.9% | -2.4 (-1.4) | -1.4 (-0.8) |
| orb30 long, 1m bars | 2194 | 51.3% | +0.019 | 49.5% | -0.001 | 48.8% | +1.8 (+1.1) | +2.6 (+1.5) |
| orb30 short, 1m bars | 2181 | 47.3% | +0.002 | 49.0% | +0.006 | 48.1% | -1.7 (-1.0) | -0.8 (-0.5) |
| gap0.5_cont long | 3193 | 48.7% | -0.010 | 49.7% | +0.009 | 49.9% | -1.0 (-0.6) | -1.1 (-0.7) |
| gap0.5_cont short | 2764 | 50.9% | +0.010 | 48.8% | -0.004 | 49.4% | +2.2 (+1.1) | +1.6 (+0.8) |
| gap0.5_fill long | 2764 | 47.6% | -0.010 | 49.4% | -0.011 | 51.2% | -1.8 (-0.9) | -3.5 (-1.8) |
| gap0.5_fill short | 3193 | 50.4% | +0.010 | 48.6% | -0.004 | 49.6% | +1.8 (+1.0) | +0.8 (+0.5) |
| gap1_cont long | 1638 | 49.0% | -0.013 | 47.8% | -0.016 | 49.1% | +1.2 (+0.5) | -0.1 (-0.1) |
| gap1_cont short | 1565 | 50.2% | +0.007 | 50.6% | +0.008 | 49.5% | -0.4 (-0.1) | +0.8 (+0.3) |
| gap1_fill long | 1565 | 47.9% | -0.007 | 50.8% | +0.017 | 50.8% | -2.9 (-1.2) | -2.9 (-1.2) |
| gap1_fill short | 1638 | 50.2% | +0.013 | 49.5% | +0.007 | 50.0% | +0.7 (+0.3) | +0.2 (+0.1) |
| first_half_hour long | 3695 | 50.0% | +0.006 | 49.0% | -0.006 | 48.7% | +1.0 (+0.6) | +1.3 (+0.8) |
| first_half_hour short | 3244 | 52.3% | +0.035 | 50.0% | +0.011 | 49.4% | +2.3 (+1.3) | +2.9 (+1.6) |

With the random-direction control instead (all other parts of the bar except the year test unchanged), rows meeting the 3-standard-error bar at both 10 and 30 minutes with a positive average move in both all9 and spy: none.

## What changed from T10

Rules, bar sizes, universes, noise (clustered by day) and the pass bar are unchanged. Two things changed:
- **Control:** a random entry on the same name, at the same time of day within ±5 minutes, on a different random
  trading day of the same year, never the signal's own day. The pass bar uses the control taken the same way as
  the signal. The random-direction version is kept for the drift comparison.
- **FOMC decision days skipped:** 40 days in 2019-2023, from the Federal Reserve's website.

T10 (https://github.com/Trader-Ed/trading-results/blob/main/history/2026-10-28-t10-research-bench.md) stays as
published. The bench's rules are the ones verified there against the live rules and the October 27 test.

## Method

- **Data:** Alpaca 1-minute SIP bars, split-adjusted, regular session only, AAPL, AMZN, NVDA, MSFT, META, GOOGL, TSLA, SPY and QQQ. Research years 2019-2023 only; 2024-2025 is the holdout and was not used. Indicators run on the continuous regular-session series (the previous sessions warm them up).
- **Bar sizes:** 2-, 3-, 4- and 5-minute bars are built from the 1-minute bars, aligned to 9:30. Every rule decides at a bar's close; moves are measured from that close in minutes, on the 1-minute prices (the price at time T is the close of the last 1-minute bar ending by T).
- **Rules:** the current rulebook's squeeze rule (breakout) and pullback rules (with the chop filter and the VWAP warm-up to 10:00), and Ed's rules with the T9 definitions, each tested on its own (no squeeze priority, no 10:00 squeeze-only limit), with the bar size as a setting; entries decided 9:35-11:50. A repeat of the same rule and side within 5 minutes of the last recorded one is skipped (as in T9). Opening-range breakout: range 9:30-9:45 or 9:30-10:00, the first later bar (1- or 5-minute) decided by 11:30 that closes beyond the range with volume at least 1.5× the range's average bar volume, one per day. Gap: 9:30 open vs the prior close; continuation and fill at the 9:35 close. First half hour: 9:30 open to 10:00 moves at least 0.3%; signal at 10:00.
- **Control (T10b):** for each signal, a random entry on the same name at the same time of day within ±5 minutes (kept within 9:35-11:50), on a different random trading day of the same year, never the signal's own day. Two versions are kept: random direction, and taken the same way as the signal (long signals vs the control taken long, short vs taken short), which removes the market's drift. The same-way comparison decides the pass bar.
- **FOMC days:** the 40 FOMC decision days in 2019-2023 are skipped as the live rulebook skips them (no signals; no controls drawn from them): 40 of 1,258 sessions. Dates from the Federal Reserve's website, listed in backtest/bench/config.yaml (the 2nd day of each scheduled meeting, plus the unscheduled rate cut released 2020-03-03).
- **Noise:** every standard error (±) is clustered by day: signals on the same day, on any name, count as one cluster. The share gap's standard error uses the paired difference between each signal and its own control. z = gap / its standard error.
- **Universes:** all9 (every name, every day), spy (SPY only), atr_pick (the rulebook's weekday universe and ATR % pick, from daily bars built from the regular session; FOMC days skipped as above).
- **Pass bar (fixed in advance):** at least 300 signals; the share moving our way beats the control taken the same way by at least 3 standard errors at both 10 and 30 minutes; the average move our way is positive at both; it holds in at least 4 of the 5 years (a year holds when the share beats the control and the average move is positive at both 10 and 30 minutes); and it holds in both all9 and spy. Options-worthy: at least 57% our way at 30 minutes and an average move of at least 0.15% at 30 minutes, in both universes.

## all9: every name, every day

| Rule | Count | Days | Our way 10m | Ctrl 10m | Gap 10m (z) | Our way 30m | Ctrl 30m | Gap 30m (z) | Avg 10m % | Avg 30m % | Years held | Meets bar | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 2052 | 902 | 50.2% ±1.2 | 51.5% | -1.3 (-0.8) | 49.8% ±1.3 | 52.5% | -2.7 (-1.6) | +0.009 ±0.007 | +0.001 ±0.012 | 1/5 | no | FAIL |
| squeeze short, 1m bars | 1873 | 866 | 48.6% ±1.4 | 48.1% | +0.5 (+0.3) | 49.1% ±1.4 | 47.0% | +2.0 (+1.1) | +0.019 ±0.009 | +0.026 ±0.015 | 1/5 | no | FAIL |
| squeeze long, 2m bars | 777 | 503 | 52.6% ±1.9 | 49.2% | +3.5 (+1.4) | 51.9% ±2.0 | 50.3% | +1.5 (+0.6) | +0.027 ±0.013 | +0.042 ±0.023 | 3/5 | no | FAIL |
| squeeze short, 2m bars | 660 | 442 | 48.0% ±2.1 | 48.3% | -0.3 (-0.1) | 47.6% ±2.2 | 46.5% | +1.1 (+0.4) | +0.029 ±0.012 | +0.038 ±0.024 | 1/5 | no | FAIL |
| squeeze long, 3m bars | 544 | 372 | 51.7% ±2.3 | 42.8% | +8.8 (+2.7) | 52.2% ±2.4 | 50.6% | +1.7 (+0.5) | +0.039 ±0.019 | +0.090 ±0.034 | 2/5 | no | FAIL |
| squeeze short, 3m bars | 486 | 325 | 50.0% ±2.7 | 49.2% | +0.8 (+0.2) | 49.0% ±2.6 | 52.7% | -3.7 (-1.1) | -0.016 ±0.028 | -0.011 ±0.036 | 2/5 | no | FAIL |
| squeeze long, 4m bars | 526 | 346 | 54.2% ±2.4 | 50.2% | +4.0 (+1.2) | 52.5% ±2.5 | 49.4% | +3.0 (+1.0) | +0.053 ±0.024 | +0.083 ±0.043 | 2/5 | no | FAIL |
| squeeze short, 4m bars | 405 | 262 | 50.4% ±3.2 | 48.4% | +2.0 (+0.5) | 51.6% ±2.9 | 47.9% | +3.7 (+1.0) | +0.002 ±0.039 | +0.001 ±0.050 | 2/5 | no | FAIL |
| squeeze long, 5m bars | 693 | 373 | 48.8% ±2.3 | 51.8% | -3.0 (-1.1) | 50.8% ±2.2 | 50.8% | +0.0 (+0.0) | +0.001 ±0.027 | +0.022 ±0.039 | 2/5 | no | FAIL |
| squeeze short, 5m bars | 599 | 359 | 49.2% ±2.5 | 47.6% | +1.7 (+0.5) | 48.4% ±2.4 | 46.9% | +1.5 (+0.5) | -0.019 ±0.028 | +0.011 ±0.047 | 0/5 | no | FAIL |
| pullback long, 1m bars | 2888 | 949 | 50.1% ±1.0 | 50.8% | -0.7 (-0.5) | 50.5% ±1.1 | 50.2% | +0.3 (+0.2) | +0.007 ±0.006 | +0.024 ±0.012 | 1/5 | no | FAIL |
| pullback short, 1m bars | 2347 | 912 | 47.3% ±1.2 | 47.6% | -0.3 (-0.2) | 46.1% ±1.3 | 48.2% | -2.1 (-1.2) | -0.005 ±0.007 | -0.015 ±0.012 | 0/5 | no | FAIL |
| pullback long, 2m bars | 922 | 586 | 51.1% ±1.7 | 49.0% | +2.1 (+0.9) | 49.6% ±1.7 | 51.1% | -1.5 (-0.6) | +0.005 ±0.013 | -0.001 ±0.021 | 1/5 | no | FAIL |
| pullback short, 2m bars | 761 | 507 | 46.0% ±2.0 | 50.3% | -4.3 (-1.6) | 47.2% ±2.0 | 49.8% | -2.6 (-1.0) | -0.005 ±0.013 | -0.008 ±0.020 | 0/5 | no | FAIL |
| pullback long, 3m bars | 534 | 402 | 49.6% ±2.2 | 52.2% | -2.6 (-0.8) | 50.2% ±2.3 | 50.2% | +0.0 (+0.0) | +0.027 ±0.022 | +0.046 ±0.037 | 1/5 | no | FAIL |
| pullback short, 3m bars | 445 | 345 | 50.6% ±2.5 | 47.9% | +2.7 (+0.8) | 46.3% ±2.5 | 50.6% | -4.3 (-1.2) | -0.017 ±0.020 | -0.029 ±0.034 | 1/5 | no | FAIL |
| pullback long, 4m bars | 375 | 297 | 47.5% ±2.7 | 49.6% | -2.1 (-0.6) | 46.4% ±2.8 | 51.2% | -4.8 (-1.3) | -0.031 ±0.029 | -0.046 ±0.043 | 0/5 | no | FAIL |
| pullback short, 4m bars | 357 | 288 | 52.1% ±2.7 | 46.8% | +5.3 (+1.3) | 50.4% ±2.9 | 48.5% | +2.0 (+0.6) | +0.013 ±0.027 | +0.045 ±0.047 | 1/5 | no | FAIL |
| pullback long, 5m bars | 468 | 331 | 48.7% ±2.5 | 48.9% | -0.2 (-0.1) | 47.6% ±2.5 | 49.6% | -1.9 (-0.6) | -0.023 ±0.027 | -0.054 ±0.043 | 0/5 | no | FAIL |
| pullback short, 5m bars | 477 | 356 | 50.7% ±2.4 | 48.8% | +1.9 (+0.6) | 50.9% ±2.5 | 52.6% | -1.7 (-0.5) | +0.025 ±0.022 | +0.014 ±0.043 | 3/5 | no | FAIL |
| e1_trend long, 1m bars | 57035 | 1218 | 50.1% ±0.4 | 50.0% | +0.1 (+0.2) | 50.3% ±0.5 | 50.7% | -0.4 (-0.7) | +0.003 ±0.003 | +0.006 ±0.006 | 1/5 | no | FAIL |
| e1_trend short, 1m bars | 54931 | 1218 | 48.5% ±0.4 | 48.7% | -0.2 (-0.4) | 48.2% ±0.5 | 48.1% | +0.1 (+0.2) | -0.002 ±0.003 | -0.007 ±0.006 | 0/5 | no | FAIL |
| e1_trend long, 2m bars | 28704 | 1217 | 49.5% ±0.4 | 50.3% | -0.9 (-1.7) | 50.3% ±0.6 | 50.9% | -0.6 (-1.0) | -0.000 ±0.003 | +0.007 ±0.007 | 1/5 | no | FAIL |
| e1_trend short, 2m bars | 27566 | 1216 | 48.6% ±0.5 | 48.4% | +0.2 (+0.3) | 47.9% ±0.6 | 48.5% | -0.6 (-0.8) | -0.001 ±0.003 | -0.004 ±0.007 | 1/5 | no | FAIL |
| e1_trend long, 3m bars | 18663 | 1203 | 49.8% ±0.5 | 50.2% | -0.4 (-0.7) | 49.9% ±0.6 | 50.5% | -0.6 (-0.9) | +0.001 ±0.004 | +0.005 ±0.008 | 1/5 | no | FAIL |
| e1_trend short, 3m bars | 17802 | 1210 | 48.4% ±0.5 | 48.2% | +0.2 (+0.2) | 48.5% ±0.7 | 48.8% | -0.3 (-0.4) | -0.004 ±0.004 | -0.004 ±0.008 | 1/5 | no | FAIL |
| e1_trend long, 4m bars | 13617 | 1187 | 49.6% ±0.5 | 49.8% | -0.2 (-0.3) | 49.4% ±0.7 | 50.2% | -0.8 (-1.0) | -0.001 ±0.004 | -0.003 ±0.008 | 0/5 | no | FAIL |
| e1_trend short, 4m bars | 13108 | 1198 | 48.1% ±0.6 | 48.3% | -0.3 (-0.4) | 48.6% ±0.7 | 48.4% | +0.2 (+0.2) | -0.004 ±0.005 | -0.006 ±0.009 | 2/5 | no | FAIL |
| e1_trend long, 5m bars | 12501 | 1176 | 49.0% ±0.6 | 49.1% | -0.1 (-0.2) | 49.2% ±0.7 | 50.6% | -1.5 (-1.7) | -0.007 ±0.005 | -0.002 ±0.009 | 1/5 | no | FAIL |
| e1_trend short, 5m bars | 11872 | 1175 | 47.6% ±0.6 | 48.5% | -0.8 (-1.1) | 48.6% ±0.8 | 48.6% | -0.1 (-0.1) | -0.012 ±0.005 | -0.008 ±0.010 | 0/5 | no | FAIL |
| e1_reject long, 1m bars | 90864 | 1218 | 49.6% ±0.3 | 50.1% | -0.5 (-1.4) | 50.5% ±0.5 | 50.9% | -0.4 (-0.8) | +0.003 ±0.002 | +0.007 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 1m bars | 84770 | 1218 | 48.1% ±0.4 | 48.3% | -0.2 (-0.6) | 48.2% ±0.5 | 48.4% | -0.2 (-0.4) | -0.001 ±0.003 | -0.003 ±0.006 | 1/5 | no | FAIL |
| e1_reject long, 2m bars | 63377 | 1216 | 49.3% ±0.4 | 50.1% | -0.8 (-2.0) | 50.3% ±0.6 | 51.1% | -0.8 (-1.3) | +0.002 ±0.002 | +0.007 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 2m bars | 56950 | 1217 | 48.1% ±0.4 | 48.4% | -0.3 (-0.8) | 47.8% ±0.6 | 48.3% | -0.5 (-0.7) | -0.000 ±0.003 | -0.002 ±0.007 | 0/5 | no | FAIL |
| e1_reject long, 3m bars | 48025 | 1202 | 49.7% ±0.4 | 50.2% | -0.5 (-1.2) | 50.3% ±0.6 | 51.0% | -0.7 (-1.1) | +0.001 ±0.003 | +0.006 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 3m bars | 42696 | 1206 | 48.0% ±0.4 | 48.3% | -0.3 (-0.6) | 47.8% ±0.6 | 48.2% | -0.4 (-0.6) | -0.005 ±0.003 | -0.007 ±0.007 | 0/5 | no | FAIL |
| e1_reject long, 4m bars | 35042 | 1182 | 49.9% ±0.4 | 50.4% | -0.4 (-0.8) | 50.5% ±0.6 | 51.0% | -0.5 (-0.8) | +0.002 ±0.003 | +0.006 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 4m bars | 30743 | 1186 | 48.2% ±0.5 | 48.4% | -0.2 (-0.4) | 47.8% ±0.7 | 47.9% | -0.1 (-0.1) | -0.004 ±0.003 | -0.005 ±0.008 | 1/5 | no | FAIL |
| e1_reject long, 5m bars | 27672 | 1165 | 49.4% ±0.4 | 50.1% | -0.7 (-1.2) | 50.2% ±0.6 | 50.7% | -0.5 (-0.7) | +0.001 ±0.003 | +0.008 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 5m bars | 24300 | 1163 | 48.1% ±0.5 | 48.4% | -0.3 (-0.6) | 47.7% ±0.7 | 48.4% | -0.6 (-0.8) | -0.006 ±0.004 | -0.003 ±0.008 | 0/5 | no | FAIL |
| r2_rsi long, 1m bars | 14006 | 1181 | 50.2% ±0.6 | 49.6% | +0.6 (+0.8) | 50.5% ±0.8 | 50.0% | +0.4 (+0.5) | -0.003 ±0.005 | -0.004 ±0.011 | 2/5 | no | FAIL |
| r2_rsi short, 1m bars | 9249 | 1144 | 47.5% ±0.7 | 48.9% | -1.4 (-1.7) | 47.8% ±0.8 | 48.9% | -1.1 (-1.1) | -0.013 ±0.005 | -0.014 ±0.010 | 1/5 | no | FAIL |
| r2_rsi long, 2m bars | 8765 | 1046 | 49.2% ±0.8 | 49.9% | -0.7 (-0.7) | 49.7% ±1.0 | 50.8% | -1.1 (-1.0) | -0.007 ±0.007 | -0.002 ±0.013 | 1/5 | no | FAIL |
| r2_rsi short, 2m bars | 5695 | 1015 | 46.9% ±0.8 | 48.1% | -1.2 (-1.2) | 46.7% ±1.0 | 49.1% | -2.4 (-2.0) | -0.024 ±0.006 | -0.033 ±0.012 | 0/5 | no | FAIL |
| r2_rsi long, 3m bars | 7585 | 970 | 48.8% ±0.9 | 48.8% | -0.0 (-0.0) | 48.9% ±1.0 | 50.7% | -1.8 (-1.5) | -0.009 ±0.007 | -0.009 ±0.014 | 1/5 | no | FAIL |
| r2_rsi short, 3m bars | 4346 | 935 | 46.1% ±0.9 | 48.5% | -2.4 (-2.1) | 45.7% ±1.1 | 49.5% | -3.9 (-3.0) | -0.022 ±0.007 | -0.039 ±0.014 | 0/5 | no | FAIL |
| r2_rsi long, 4m bars | 6266 | 920 | 49.4% ±0.9 | 50.7% | -1.3 (-1.2) | 50.3% ±1.1 | 50.4% | -0.1 (-0.1) | -0.008 ±0.008 | +0.003 ±0.015 | 0/5 | no | FAIL |
| r2_rsi short, 4m bars | 3633 | 888 | 44.9% ±1.0 | 49.3% | -4.4 (-3.2) | 47.2% ±1.1 | 47.6% | -0.4 (-0.3) | -0.017 ±0.008 | -0.024 ±0.014 | 0/5 | no | FAIL |
| r2_rsi long, 5m bars | 5588 | 903 | 48.2% ±1.0 | 50.0% | -1.8 (-1.6) | 48.9% ±1.1 | 50.9% | -2.1 (-1.6) | -0.020 ±0.008 | -0.015 ±0.015 | 0/5 | no | FAIL |
| r2_rsi short, 5m bars | 3211 | 861 | 46.6% ±1.1 | 48.3% | -1.7 (-1.2) | 46.4% ±1.2 | 48.3% | -1.9 (-1.3) | -0.015 ±0.008 | -0.014 ±0.015 | 1/5 | no | FAIL |
| r2_rsi_sym long, 1m bars | 8065 | 1124 | 51.4% ±0.8 | 50.1% | +1.3 (+1.3) | 51.1% ±0.9 | 50.7% | +0.3 (+0.3) | +0.000 ±0.006 | +0.003 ±0.013 | 3/5 | no | FAIL |
| r2_rsi_sym short, 1m bars | 9249 | 1144 | 47.5% ±0.7 | 49.1% | -1.6 (-1.9) | 47.8% ±0.8 | 48.4% | -0.6 (-0.6) | -0.013 ±0.005 | -0.014 ±0.010 | 1/5 | no | FAIL |
| r2_rsi_sym long, 2m bars | 4760 | 936 | 49.6% ±1.0 | 48.8% | +0.8 (+0.6) | 50.5% ±1.1 | 50.1% | +0.4 (+0.3) | -0.001 ±0.009 | +0.006 ±0.015 | 1/5 | no | FAIL |
| r2_rsi_sym short, 2m bars | 5695 | 1015 | 46.9% ±0.8 | 49.2% | -2.3 (-2.2) | 46.7% ±1.0 | 49.0% | -2.3 (-1.9) | -0.024 ±0.006 | -0.033 ±0.012 | 0/5 | no | FAIL |
| r2_rsi_sym long, 3m bars | 3791 | 847 | 48.9% ±1.1 | 49.7% | -0.8 (-0.6) | 49.7% ±1.2 | 49.8% | -0.2 (-0.1) | -0.013 ±0.009 | +0.002 ±0.016 | 0/5 | no | FAIL |
| r2_rsi_sym short, 3m bars | 4346 | 935 | 46.1% ±0.9 | 48.2% | -2.1 (-1.8) | 45.7% ±1.1 | 47.7% | -2.1 (-1.6) | -0.022 ±0.007 | -0.039 ±0.014 | 0/5 | no | FAIL |
| r2_rsi_sym long, 4m bars | 3077 | 786 | 51.0% ±1.1 | 50.1% | +0.9 (+0.6) | 51.3% ±1.3 | 51.5% | -0.3 (-0.2) | +0.005 ±0.010 | +0.020 ±0.017 | 2/5 | no | FAIL |
| r2_rsi_sym short, 4m bars | 3633 | 888 | 44.9% ±1.0 | 48.9% | -4.0 (-3.1) | 47.2% ±1.1 | 48.2% | -1.0 (-0.7) | -0.017 ±0.008 | -0.024 ±0.014 | 0/5 | no | FAIL |
| r2_rsi_sym long, 5m bars | 2793 | 770 | 49.9% ±1.2 | 50.0% | -0.1 (-0.1) | 49.7% ±1.3 | 50.3% | -0.6 (-0.4) | -0.016 ±0.011 | -0.010 ±0.017 | 0/5 | no | FAIL |
| r2_rsi_sym short, 5m bars | 3211 | 861 | 46.6% ±1.1 | 47.4% | -0.9 (-0.6) | 46.4% ±1.2 | 47.1% | -0.7 (-0.5) | -0.015 ±0.008 | -0.014 ±0.015 | 1/5 | no | FAIL |
| b3_touch long, 1m bars | 85790 | 1218 | 50.6% ±0.3 | 50.3% | +0.3 (+0.8) | 51.2% ±0.5 | 51.0% | +0.2 (+0.4) | +0.006 ±0.002 | +0.005 ±0.006 | 4/5 | no | FAIL |
| b3_touch short, 1m bars | 88480 | 1218 | 48.4% ±0.3 | 48.5% | -0.1 (-0.2) | 48.5% ±0.5 | 48.1% | +0.4 (+0.7) | -0.003 ±0.002 | -0.006 ±0.005 | 0/5 | no | FAIL |
| b3_touch long, 2m bars | 58934 | 1218 | 51.0% ±0.4 | 50.3% | +0.7 (+1.7) | 51.5% ±0.6 | 51.2% | +0.3 (+0.4) | +0.004 ±0.003 | +0.002 ±0.007 | 3/5 | no | FAIL |
| b3_touch short, 2m bars | 60958 | 1218 | 48.7% ±0.4 | 48.3% | +0.4 (+1.0) | 48.6% ±0.6 | 48.3% | +0.3 (+0.5) | -0.005 ±0.003 | -0.008 ±0.006 | 0/5 | no | FAIL |
| b3_touch long, 3m bars | 47313 | 1215 | 50.5% ±0.4 | 49.8% | +0.7 (+1.4) | 51.3% ±0.6 | 50.6% | +0.7 (+1.1) | +0.002 ±0.004 | +0.002 ±0.008 | 3/5 | no | FAIL |
| b3_touch short, 3m bars | 49825 | 1215 | 48.7% ±0.4 | 48.0% | +0.7 (+1.3) | 48.5% ±0.6 | 47.9% | +0.6 (+0.9) | -0.004 ±0.003 | -0.011 ±0.007 | 0/5 | no | FAIL |
| b3_touch long, 4m bars | 33834 | 1204 | 50.4% ±0.5 | 50.2% | +0.2 (+0.4) | 51.2% ±0.7 | 51.1% | +0.1 (+0.1) | -0.000 ±0.004 | +0.004 ±0.009 | 2/5 | no | FAIL |
| b3_touch short, 4m bars | 35588 | 1199 | 48.5% ±0.5 | 49.0% | -0.5 (-0.9) | 48.4% ±0.6 | 48.9% | -0.5 (-0.7) | -0.006 ±0.004 | -0.011 ±0.008 | 0/5 | no | FAIL |
| b3_touch long, 5m bars | 28366 | 1196 | 50.3% ±0.5 | 50.4% | -0.1 (-0.1) | 51.0% ±0.7 | 50.7% | +0.3 (+0.4) | +0.003 ±0.004 | +0.005 ±0.010 | 1/5 | no | FAIL |
| b3_touch short, 5m bars | 30468 | 1189 | 48.7% ±0.5 | 48.3% | +0.4 (+0.7) | 48.4% ±0.7 | 48.3% | +0.1 (+0.2) | -0.007 ±0.004 | -0.015 ±0.009 | 0/5 | no | FAIL |
| b3_reentry long, 1m bars | 33096 | 1218 | 50.9% ±0.4 | 50.6% | +0.3 (+0.6) | 51.5% ±0.6 | 51.3% | +0.1 (+0.2) | +0.006 ±0.003 | +0.005 ±0.007 | 2/5 | no | FAIL |
| b3_reentry short, 1m bars | 32355 | 1218 | 48.6% ±0.4 | 48.4% | +0.2 (+0.5) | 48.4% ±0.5 | 48.1% | +0.4 (+0.6) | -0.005 ±0.003 | -0.007 ±0.007 | 1/5 | no | FAIL |
| b3_reentry long, 2m bars | 19081 | 1214 | 50.5% ±0.6 | 49.5% | +1.0 (+1.5) | 51.0% ±0.7 | 50.3% | +0.8 (+1.0) | -0.000 ±0.005 | -0.002 ±0.009 | 3/5 | no | FAIL |
| b3_reentry short, 2m bars | 19087 | 1214 | 49.3% ±0.5 | 49.0% | +0.3 (+0.4) | 48.5% ±0.7 | 48.6% | -0.1 (-0.1) | -0.006 ±0.005 | -0.014 ±0.009 | 1/5 | no | FAIL |
| b3_reentry long, 3m bars | 13897 | 1188 | 49.8% ±0.7 | 49.8% | -0.0 (-0.0) | 50.7% ±0.8 | 49.6% | +1.1 (+1.3) | +0.000 ±0.006 | +0.003 ±0.011 | 2/5 | no | FAIL |
| b3_reentry short, 3m bars | 14186 | 1192 | 48.5% ±0.6 | 48.8% | -0.2 (-0.3) | 48.3% ±0.8 | 48.6% | -0.4 (-0.4) | -0.004 ±0.006 | -0.014 ±0.011 | 0/5 | no | FAIL |
| b3_reentry long, 4m bars | 10721 | 1158 | 49.8% ±0.7 | 49.9% | -0.1 (-0.2) | 50.9% ±0.9 | 50.2% | +0.7 (+0.7) | -0.004 ±0.006 | +0.007 ±0.013 | 2/5 | no | FAIL |
| b3_reentry short, 4m bars | 11055 | 1162 | 48.9% ±0.7 | 48.5% | +0.4 (+0.4) | 48.6% ±0.8 | 48.8% | -0.2 (-0.2) | -0.005 ±0.006 | -0.007 ±0.011 | 1/5 | no | FAIL |
| b3_reentry long, 5m bars | 9646 | 1130 | 49.2% ±0.8 | 49.3% | -0.1 (-0.1) | 51.0% ±0.9 | 49.1% | +1.8 (+1.8) | -0.013 ±0.007 | +0.008 ±0.013 | 1/5 | no | FAIL |
| b3_reentry short, 5m bars | 10048 | 1145 | 47.9% ±0.7 | 48.8% | -0.8 (-1.0) | 49.0% ±0.8 | 48.9% | +0.1 (+0.1) | -0.005 ±0.006 | -0.010 ±0.012 | 1/5 | no | FAIL |
| orb15 long, 1m bars | 2084 | 836 | 50.9% ±1.2 | 50.9% | -0.0 (-0.0) | 52.6% ±1.4 | 51.1% | +1.5 (+0.9) | +0.025 ±0.011 | +0.041 ±0.016 | 2/5 | no | FAIL |
| orb15 short, 1m bars | 1939 | 756 | 46.4% ±1.3 | 48.8% | -2.4 (-1.4) | 48.9% ±1.5 | 47.7% | +1.2 (+0.6) | -0.015 ±0.015 | -0.003 ±0.020 | 0/5 | no | FAIL |
| orb15 long, 5m bars | 315 | 226 | 50.5% ±3.2 | 57.8% | -7.3 (-1.7) | 52.7% ±3.2 | 61.0% | -8.3 (-2.0) | -0.008 ±0.024 | +0.037 ±0.037 | 0/5 | no | FAIL |
| orb15 short, 5m bars | 368 | 234 | 50.3% ±2.8 | 50.0% | +0.3 (+0.1) | 49.5% ±3.0 | 50.8% | -1.4 (-0.4) | +0.006 ±0.039 | +0.014 ±0.044 | 1/5 | no | FAIL |
| orb30 long, 1m bars | 2194 | 816 | 51.3% ±1.2 | 49.5% | +1.8 (+1.1) | 53.0% ±1.3 | 52.0% | +1.0 (+0.6) | +0.019 ±0.009 | +0.025 ±0.015 | 3/5 | no | FAIL |
| orb30 short, 1m bars | 2181 | 736 | 47.3% ±1.4 | 49.0% | -1.7 (-1.0) | 47.9% ±1.5 | 49.0% | -1.1 (-0.6) | +0.002 ±0.011 | +0.018 ±0.017 | 1/5 | no | FAIL |
| orb30 long, 5m bars | 393 | 289 | 51.9% ±2.9 | 51.7% | +0.3 (+0.1) | 55.0% ±2.8 | 51.4% | +3.6 (+1.0) | -0.009 ±0.019 | -0.014 ±0.034 | 0/5 | no | FAIL |
| orb30 short, 5m bars | 461 | 271 | 49.9% ±2.6 | 48.6% | +1.3 (+0.4) | 48.4% ±2.9 | 51.4% | -3.0 (-0.9) | -0.010 ±0.020 | +0.012 ±0.033 | 0/5 | no | FAIL |
| gap0.5_cont long | 3193 | 806 | 48.7% ±1.5 | 49.7% | -1.0 (-0.6) | 53.0% ±1.5 | 51.1% | +1.9 (+1.1) | -0.010 ±0.020 | +0.036 ±0.029 | 1/5 | no | FAIL |
| gap0.5_cont short | 2764 | 688 | 50.9% ±1.7 | 48.8% | +2.2 (+1.1) | 55.2% ±1.7 | 50.4% | +4.9 (+2.5) | +0.010 ±0.023 | +0.047 ±0.037 | 1/5 | no | FAIL |
| gap0.5_fill long | 2764 | 688 | 47.6% ±1.7 | 49.4% | -1.8 (-0.9) | 43.9% ±1.7 | 49.1% | -5.2 (-2.7) | -0.010 ±0.023 | -0.047 ±0.037 | 0/5 | no | FAIL |
| gap0.5_fill short | 3193 | 806 | 50.4% ±1.5 | 48.6% | +1.8 (+1.0) | 46.6% ±1.5 | 49.5% | -2.9 (-1.7) | +0.010 ±0.020 | -0.036 ±0.029 | 0/5 | no | FAIL |
| gap1_cont long | 1638 | 578 | 49.0% ±1.9 | 47.8% | +1.2 (+0.5) | 54.9% ±1.9 | 50.3% | +4.6 (+1.9) | -0.013 ±0.031 | +0.072 ±0.045 | 1/5 | no | FAIL |
| gap1_cont short | 1565 | 494 | 50.2% ±2.2 | 50.6% | -0.4 (-0.1) | 54.7% ±2.2 | 49.9% | +4.8 (+1.9) | +0.007 ±0.032 | +0.036 ±0.052 | 1/5 | no | FAIL |
| gap1_fill long | 1565 | 494 | 47.9% ±2.2 | 50.8% | -2.9 (-1.2) | 44.5% ±2.2 | 50.4% | -5.9 (-2.4) | -0.007 ±0.032 | -0.036 ±0.052 | 0/5 | no | FAIL |
| gap1_fill short | 1638 | 578 | 50.2% ±1.9 | 49.5% | +0.7 (+0.3) | 44.7% ±1.9 | 49.4% | -4.7 (-1.9) | +0.013 ±0.031 | -0.072 ±0.045 | 0/5 | no | FAIL |
| first_half_hour long | 3695 | 1009 | 50.0% ±1.4 | 49.0% | +1.0 (+0.6) | 52.2% ±1.4 | 51.4% | +0.8 (+0.5) | +0.006 ±0.013 | +0.029 ±0.019 | 2/5 | no | FAIL |
| first_half_hour short | 3244 | 948 | 52.3% ±1.5 | 50.0% | +2.3 (+1.3) | 50.2% ±1.5 | 49.1% | +1.1 (+0.6) | +0.035 ±0.015 | +0.000 ±0.025 | 2/5 | no | FAIL |

Gap and first-half-hour rules at their extra horizons (control over the same number of minutes):

| Rule | Count | +5m: our way (ctrl), avg % | to 10:00: our way (ctrl), avg % | to 10:30: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|---|---|
| gap0.5_cont long | 3193 | 49.1% (49.1%, z +0.0), -0.017 ±0.015 | 52.6% (51.4%, z +0.7), +0.022 ±0.027 | 52.0% (51.1%, z +0.5), +0.031 ±0.035 | 52.0% (50.4%, z +0.9), +0.044 ±0.036 | 52.5% (50.0%, z +1.4), +0.068 ±0.050 |
| gap0.5_cont short | 2764 | 47.3% (49.4%, z -1.1), -0.017 ±0.017 | 51.8% (49.0%, z +1.4), -0.014 ±0.034 | 50.6% (49.0%, z +0.8), -0.034 ±0.047 | 50.8% (48.6%, z +1.1), -0.020 ±0.050 | 50.7% (48.7%, z +1.0), -0.040 ±0.062 |
| gap0.5_fill long | 2764 | 51.2% (49.5%, z +0.9), +0.017 ±0.017 | 47.9% (50.2%, z -1.2), +0.014 ±0.034 | 49.2% (50.4%, z -0.6), +0.034 ±0.047 | 48.9% (50.1%, z -0.6), +0.020 ±0.050 | 49.0% (50.9%, z -0.9), +0.040 ±0.062 |
| gap0.5_fill short | 3193 | 50.0% (47.6%, z +1.4), +0.017 ±0.015 | 46.8% (48.1%, z -0.7), -0.022 ±0.027 | 47.6% (48.7%, z -0.6), -0.031 ±0.035 | 47.7% (48.9%, z -0.7), -0.044 ±0.036 | 47.2% (48.2%, z -0.6), -0.068 ±0.050 |
| gap1_cont long | 1638 | 48.1% (49.0%, z -0.4), -0.030 ±0.023 | 53.9% (50.3%, z +1.5), +0.043 ±0.042 | 52.6% (51.3%, z +0.6), +0.055 ±0.051 | 52.6% (51.2%, z +0.6), +0.076 ±0.052 | 52.4% (50.7%, z +0.7), +0.103 ±0.075 |
| gap1_cont short | 1565 | 46.6% (48.9%, z -1.0), -0.032 ±0.024 | 50.4% (49.7%, z +0.3), -0.046 ±0.048 | 51.3% (49.6%, z +0.6), -0.065 ±0.066 | 51.3% (49.6%, z +0.6), -0.047 ±0.070 | 51.6% (50.5%, z +0.4), -0.059 ±0.091 |
| gap1_fill long | 1565 | 51.4% (50.9%, z +0.2), +0.032 ±0.024 | 49.1% (51.1%, z -0.8), +0.046 ±0.048 | 48.5% (52.1%, z -1.4), +0.065 ±0.066 | 48.4% (51.8%, z -1.3), +0.047 ±0.070 | 48.0% (50.5%, z -0.9), +0.059 ±0.091 |
| gap1_fill short | 1638 | 51.0% (49.6%, z +0.6), +0.030 ±0.023 | 45.7% (48.3%, z -1.1), -0.043 ±0.042 | 47.0% (48.8%, z -0.7), -0.055 ±0.051 | 47.2% (49.3%, z -0.9), -0.076 ±0.052 | 47.3% (49.3%, z -0.8), -0.103 ±0.075 |

| Rule | Count | +5m: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|
| first_half_hour long | 3695 | 47.9% (48.4%, z -0.3), -0.006 ±0.011 | 51.9% (50.8%, z +0.7), +0.040 ±0.025 | 53.6% (51.7%, z +1.1), +0.093 ±0.034 |
| first_half_hour short | 3244 | 52.0% (49.8%, z +1.2), +0.033 ±0.012 | 51.2% (49.0%, z +1.2), +0.038 ±0.034 | 50.4% (48.9%, z +0.8), +0.027 ±0.044 |

## spy: SPY only

| Rule | Count | Days | Our way 10m | Ctrl 10m | Gap 10m (z) | Our way 30m | Ctrl 30m | Gap 30m (z) | Avg 10m % | Avg 30m % | Years held | Meets bar | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 216 | 205 | 45.8% ±3.4 | 56.5% | -10.6 (-2.3) | 50.0% ±3.4 | 50.9% | -0.9 (-0.2) | -0.004 ±0.008 | +0.006 ±0.014 | 0/5 | no | FAIL |
| squeeze short, 1m bars | 187 | 170 | 46.5% ±3.8 | 49.2% | -2.7 (-0.5) | 42.2% ±3.5 | 47.1% | -4.8 (-0.9) | +0.003 ±0.012 | -0.005 ±0.018 | 0/5 | no | FAIL |
| squeeze long, 2m bars | 76 | 73 | 51.3% ±5.7 | 51.3% | +0.0 (+0.0) | 47.4% ±5.9 | 56.6% | -9.2 (-1.2) | -0.012 ±0.013 | -0.030 ±0.019 | 0/5 | no | FAIL |
| squeeze short, 2m bars | 66 | 62 | 42.4% ±5.7 | 47.0% | -4.5 (-0.6) | 37.9% ±6.0 | 39.4% | -1.5 (-0.2) | -0.005 ±0.016 | -0.039 ±0.024 | 1/5 | no | FAIL |
| squeeze long, 3m bars | 49 | 48 | 42.9% ±7.0 | 40.8% | +2.0 (+0.2) | 59.2% ±7.2 | 51.0% | +8.2 (+0.8) | -0.012 ±0.014 | +0.004 ±0.032 | 0/5 | no | FAIL |
| squeeze short, 3m bars | 44 | 44 | 45.5% ±7.6 | 43.2% | +2.3 (+0.2) | 59.1% ±7.5 | 36.4% | +22.7 (+2.3) | -0.015 ±0.025 | +0.075 ±0.040 | 0/5 | no | FAIL |
| squeeze long, 4m bars | 35 | 35 | 45.7% ±8.5 | 31.4% | +14.3 (+1.3) | 54.3% ±8.5 | 48.6% | +5.7 (+0.6) | -0.005 ±0.019 | +0.000 ±0.039 | 1/5 | no | FAIL |
| squeeze short, 4m bars | 28 | 27 | 57.1% ±9.8 | 39.3% | +17.9 (+1.6) | 53.6% ±9.3 | 46.4% | +7.1 (+0.6) | +0.072 ±0.037 | +0.053 ±0.034 | 1/5 | no | FAIL |
| squeeze long, 5m bars | 38 | 38 | 50.0% ±8.2 | 60.5% | -10.5 (-0.9) | 50.0% ±8.2 | 63.2% | -13.2 (-1.2) | -0.027 ±0.041 | -0.035 ±0.054 | 0/5 | no | FAIL |
| squeeze short, 5m bars | 42 | 42 | 47.6% ±7.8 | 40.5% | +7.1 (+0.6) | 52.4% ±7.8 | 47.6% | +4.8 (+0.4) | -0.021 ±0.022 | +0.035 ±0.036 | 0/5 | no | FAIL |
| pullback long, 1m bars | 327 | 294 | 52.9% ±2.7 | 51.7% | +1.2 (+0.3) | 53.5% ±2.9 | 56.3% | -2.8 (-0.7) | +0.001 ±0.010 | +0.004 ±0.016 | 0/5 | no | FAIL |
| pullback short, 1m bars | 282 | 232 | 47.2% ±3.0 | 47.2% | +0.0 (+0.0) | 44.3% ±3.1 | 51.8% | -7.4 (-1.7) | -0.008 ±0.010 | -0.007 ±0.016 | 1/5 | no | FAIL |
| pullback long, 2m bars | 121 | 116 | 52.1% ±4.5 | 50.4% | +1.7 (+0.2) | 58.7% ±4.6 | 57.9% | +0.8 (+0.1) | +0.005 ±0.010 | +0.039 ±0.017 | 1/5 | no | FAIL |
| pullback short, 2m bars | 109 | 100 | 36.7% ±4.6 | 51.4% | -14.7 (-2.3) | 45.0% ±5.0 | 50.5% | -5.5 (-0.8) | -0.023 ±0.014 | -0.028 ±0.023 | 0/5 | no | FAIL |
| pullback long, 3m bars | 53 | 50 | 49.1% ±7.1 | 49.1% | +0.0 (+0.0) | 45.3% ±7.3 | 49.1% | -3.8 (-0.4) | -0.002 ±0.013 | +0.000 ±0.025 | 0/5 | no | FAIL |
| pullback short, 3m bars | 42 | 40 | 47.6% ±7.4 | 47.6% | +0.0 (+0.0) | 47.6% ±7.8 | 52.4% | -4.8 (-0.5) | -0.034 ±0.027 | -0.026 ±0.046 | 0/5 | no | FAIL |
| pullback long, 4m bars | 31 | 29 | 58.1% ±9.1 | 51.6% | +6.5 (+0.5) | 45.2% ±9.7 | 54.8% | -9.7 (-0.7) | +0.000 ±0.013 | -0.008 ±0.022 | 1/5 | no | FAIL |
| pullback short, 4m bars | 17 | 16 | 41.2% ±11.6 | 52.9% | -11.8 (-0.6) | 41.2% ±12.8 | 52.9% | -11.8 (-0.6) | -0.045 ±0.041 | -0.017 ±0.104 | 0/5 | no | FAIL |
| pullback long, 5m bars | 18 | 18 | 50.0% ±12.1 | 44.4% | +5.6 (+0.4) | 44.4% ±12.1 | 66.7% | -22.2 (-1.3) | +0.019 ±0.025 | +0.001 ±0.031 | 0/5 | no | FAIL |
| pullback short, 5m bars | 22 | 22 | 31.8% ±10.2 | 36.4% | -4.5 (-0.4) | 54.5% ±10.9 | 40.9% | +13.6 (+1.0) | -0.024 ±0.021 | -0.008 ±0.048 | 0/5 | no | FAIL |
| e1_trend long, 1m bars | 6427 | 1218 | 52.0% ±0.6 | 52.3% | -0.3 (-0.3) | 52.7% ±0.8 | 53.3% | -0.6 (-0.6) | +0.001 ±0.002 | +0.005 ±0.004 | 1/5 | no | FAIL |
| e1_trend short, 1m bars | 5900 | 1213 | 47.7% ±0.7 | 48.0% | -0.4 (-0.4) | 46.8% ±0.8 | 47.3% | -0.5 (-0.5) | -0.003 ±0.002 | -0.006 ±0.005 | 0/5 | no | FAIL |
| e1_trend long, 2m bars | 3203 | 1170 | 51.3% ±0.9 | 51.9% | -0.6 (-0.5) | 52.6% ±1.0 | 53.2% | -0.6 (-0.5) | +0.000 ±0.003 | +0.004 ±0.005 | 0/5 | no | FAIL |
| e1_trend short, 2m bars | 2916 | 1111 | 45.7% ±0.9 | 46.8% | -1.1 (-0.9) | 46.3% ±1.0 | 46.9% | -0.6 (-0.4) | -0.009 ±0.003 | -0.010 ±0.006 | 0/5 | no | FAIL |
| e1_trend long, 3m bars | 2108 | 1040 | 51.1% ±1.1 | 52.9% | -1.8 (-1.2) | 52.5% ±1.1 | 54.3% | -1.9 (-1.1) | -0.001 ±0.003 | +0.009 ±0.006 | 0/5 | no | FAIL |
| e1_trend short, 3m bars | 1893 | 968 | 48.0% ±1.2 | 48.9% | -1.0 (-0.6) | 47.8% ±1.2 | 47.6% | +0.1 (+0.1) | -0.001 ±0.004 | -0.003 ±0.007 | 0/5 | no | FAIL |
| e1_trend long, 4m bars | 1534 | 916 | 49.6% ±1.3 | 50.7% | -1.1 (-0.6) | 49.8% ±1.3 | 50.1% | -0.3 (-0.1) | -0.004 ±0.004 | +0.003 ±0.007 | 1/5 | no | FAIL |
| e1_trend short, 4m bars | 1401 | 849 | 46.8% ±1.3 | 47.0% | -0.2 (-0.1) | 46.5% ±1.4 | 46.8% | -0.3 (-0.1) | -0.006 ±0.005 | -0.012 ±0.008 | 1/5 | no | FAIL |
| e1_trend long, 5m bars | 1382 | 891 | 51.1% ±1.3 | 52.0% | -0.9 (-0.5) | 50.9% ±1.4 | 53.4% | -2.5 (-1.2) | -0.003 ±0.004 | +0.002 ±0.008 | 1/5 | no | FAIL |
| e1_trend short, 5m bars | 1273 | 801 | 46.7% ±1.4 | 47.1% | -0.4 (-0.2) | 47.5% ±1.4 | 47.5% | +0.0 (+0.0) | -0.004 ±0.005 | +0.003 ±0.008 | 2/5 | no | FAIL |
| e1_reject long, 1m bars | 11557 | 1218 | 51.5% ±0.5 | 52.2% | -0.7 (-1.0) | 52.6% ±0.7 | 52.9% | -0.3 (-0.4) | +0.001 ±0.002 | +0.005 ±0.004 | 1/5 | no | FAIL |
| e1_reject short, 1m bars | 9734 | 1209 | 47.4% ±0.6 | 47.5% | -0.1 (-0.2) | 46.9% ±0.8 | 46.6% | +0.3 (+0.3) | -0.001 ±0.002 | -0.003 ±0.004 | 0/5 | no | FAIL |
| e1_reject long, 2m bars | 8609 | 1170 | 50.6% ±0.6 | 51.4% | -0.8 (-1.0) | 52.4% ±0.8 | 53.0% | -0.6 (-0.6) | +0.001 ±0.002 | +0.004 ±0.004 | 1/5 | no | FAIL |
| e1_reject short, 2m bars | 6696 | 1113 | 47.3% ±0.7 | 47.4% | -0.0 (-0.0) | 46.8% ±0.9 | 45.8% | +1.1 (+1.0) | -0.002 ±0.002 | -0.003 ±0.005 | 0/5 | no | FAIL |
| e1_reject long, 3m bars | 6736 | 1070 | 51.6% ±0.7 | 52.9% | -1.3 (-1.4) | 53.4% ±0.9 | 53.9% | -0.5 (-0.5) | +0.002 ±0.002 | +0.007 ±0.005 | 1/5 | no | FAIL |
| e1_reject short, 3m bars | 5036 | 986 | 48.0% ±0.7 | 46.9% | +1.1 (+1.1) | 46.8% ±1.0 | 46.3% | +0.5 (+0.4) | -0.004 ±0.003 | -0.008 ±0.006 | 1/5 | no | FAIL |
| e1_reject long, 4m bars | 4845 | 991 | 51.4% ±0.8 | 52.2% | -0.8 (-0.7) | 53.0% ±1.0 | 53.0% | +0.0 (+0.0) | +0.000 ±0.002 | +0.007 ±0.005 | 1/5 | no | FAIL |
| e1_reject short, 4m bars | 3614 | 890 | 47.0% ±0.8 | 48.3% | -1.2 (-1.0) | 46.6% ±1.0 | 47.2% | -0.6 (-0.5) | -0.004 ±0.003 | -0.008 ±0.006 | 1/5 | no | FAIL |
| e1_reject long, 5m bars | 3751 | 915 | 50.6% ±0.8 | 52.6% | -2.0 (-1.7) | 52.6% ±1.0 | 53.5% | -0.9 (-0.7) | +0.001 ±0.002 | +0.006 ±0.005 | 0/5 | no | FAIL |
| e1_reject short, 5m bars | 2768 | 799 | 46.2% ±0.9 | 47.1% | -0.9 (-0.7) | 46.6% ±1.1 | 47.1% | -0.5 (-0.3) | -0.007 ±0.003 | -0.005 ±0.006 | 0/5 | no | FAIL |
| r2_rsi long, 1m bars | 1736 | 804 | 50.1% ±1.3 | 51.2% | -1.0 (-0.6) | 51.6% ±1.4 | 53.5% | -2.0 (-1.1) | -0.007 ±0.005 | -0.009 ±0.009 | 1/5 | no | FAIL |
| r2_rsi short, 1m bars | 1131 | 678 | 46.2% ±1.5 | 47.5% | -1.2 (-0.6) | 45.5% ±1.6 | 45.3% | +0.3 (+0.1) | -0.002 ±0.004 | -0.001 ±0.008 | 2/5 | no | FAIL |
| r2_rsi long, 2m bars | 1096 | 569 | 50.6% ±1.6 | 49.3% | +1.4 (+0.6) | 50.3% ±1.7 | 52.0% | -1.7 (-0.8) | -0.012 ±0.006 | -0.015 ±0.011 | 0/5 | no | FAIL |
| r2_rsi short, 2m bars | 684 | 460 | 44.6% ±1.9 | 50.4% | -5.8 (-2.1) | 45.9% ±2.1 | 50.4% | -4.5 (-1.6) | -0.008 ±0.006 | -0.013 ±0.010 | 1/5 | no | FAIL |
| r2_rsi long, 3m bars | 928 | 465 | 51.0% ±1.7 | 46.8% | +4.2 (+1.7) | 50.9% ±1.9 | 49.9% | +1.0 (+0.4) | -0.009 ±0.006 | -0.009 ±0.011 | 1/5 | no | FAIL |
| r2_rsi short, 3m bars | 501 | 368 | 46.1% ±2.2 | 47.9% | -1.8 (-0.6) | 44.7% ±2.3 | 54.1% | -9.4 (-3.0) | -0.003 ±0.007 | -0.008 ±0.012 | 0/5 | no | FAIL |
| r2_rsi long, 4m bars | 745 | 404 | 51.5% ±1.9 | 53.0% | -1.5 (-0.5) | 51.4% ±2.0 | 51.9% | -0.5 (-0.2) | -0.010 ±0.007 | -0.011 ±0.012 | 0/5 | no | FAIL |
| r2_rsi short, 4m bars | 448 | 350 | 43.5% ±2.4 | 51.3% | -7.8 (-2.5) | 46.7% ±2.4 | 42.6% | +4.0 (+1.2) | -0.003 ±0.007 | -0.001 ±0.013 | 1/5 | no | FAIL |
| r2_rsi long, 5m bars | 667 | 387 | 49.2% ±1.9 | 55.8% | -6.6 (-2.3) | 47.7% ±2.2 | 55.6% | -7.9 (-2.7) | -0.016 ±0.007 | -0.032 ±0.013 | 0/5 | no | FAIL |
| r2_rsi short, 5m bars | 395 | 313 | 47.6% ±2.5 | 46.3% | +1.3 (+0.4) | 45.6% ±2.5 | 44.8% | +0.8 (+0.2) | +0.002 ±0.008 | +0.004 ±0.014 | 1/5 | no | FAIL |
| r2_rsi_sym long, 1m bars | 1001 | 623 | 51.5% ±1.6 | 53.9% | -2.4 (-1.1) | 53.5% ±1.7 | 52.3% | +1.2 (+0.5) | -0.004 ±0.005 | +0.003 ±0.011 | 0/5 | no | FAIL |
| r2_rsi_sym short, 1m bars | 1131 | 678 | 46.2% ±1.5 | 49.7% | -3.4 (-1.7) | 45.5% ±1.6 | 49.8% | -4.2 (-1.9) | -0.002 ±0.004 | -0.001 ±0.008 | 1/5 | no | FAIL |
| r2_rsi_sym long, 2m bars | 574 | 400 | 51.6% ±2.0 | 50.5% | +1.0 (+0.4) | 53.1% ±2.2 | 48.3% | +4.9 (+1.6) | -0.005 ±0.007 | +0.013 ±0.013 | 1/5 | no | FAIL |
| r2_rsi_sym short, 2m bars | 684 | 460 | 44.6% ±1.9 | 47.4% | -2.8 (-1.0) | 45.9% ±2.1 | 46.9% | -1.0 (-0.4) | -0.008 ±0.006 | -0.013 ±0.010 | 0/5 | no | FAIL |
| r2_rsi_sym long, 3m bars | 441 | 331 | 51.0% ±2.4 | 51.5% | -0.5 (-0.1) | 50.8% ±2.5 | 49.9% | +0.9 (+0.3) | -0.012 ±0.010 | -0.015 ±0.013 | 0/5 | no | FAIL |
| r2_rsi_sym short, 3m bars | 501 | 368 | 46.1% ±2.2 | 44.3% | +1.8 (+0.6) | 44.7% ±2.3 | 44.5% | +0.2 (+0.1) | -0.003 ±0.007 | -0.008 ±0.012 | 2/5 | no | FAIL |
| r2_rsi_sym long, 4m bars | 345 | 269 | 52.5% ±2.7 | 56.8% | -4.3 (-1.1) | 51.6% ±2.7 | 52.2% | -0.6 (-0.2) | -0.004 ±0.008 | -0.006 ±0.015 | 0/5 | no | FAIL |
| r2_rsi_sym short, 4m bars | 448 | 350 | 43.5% ±2.4 | 47.8% | -4.2 (-1.3) | 46.7% ±2.4 | 49.3% | -2.7 (-0.8) | -0.003 ±0.007 | -0.001 ±0.013 | 1/5 | no | FAIL |
| r2_rsi_sym long, 5m bars | 311 | 257 | 52.7% ±2.8 | 51.8% | +1.0 (+0.3) | 50.2% ±2.9 | 46.9% | +3.2 (+0.8) | -0.010 ±0.011 | -0.017 ±0.017 | 1/5 | no | FAIL |
| r2_rsi_sym short, 5m bars | 395 | 313 | 47.6% ±2.5 | 48.4% | -0.8 (-0.2) | 45.6% ±2.5 | 44.3% | +1.3 (+0.3) | +0.002 ±0.008 | +0.004 ±0.014 | 1/5 | no | FAIL |
| b3_touch long, 1m bars | 10871 | 1217 | 52.1% ±0.5 | 51.9% | +0.2 (+0.2) | 53.3% ±0.7 | 53.1% | +0.2 (+0.3) | +0.003 ±0.002 | +0.004 ±0.004 | 2/5 | no | FAIL |
| b3_touch short, 1m bars | 12082 | 1217 | 47.6% ±0.5 | 47.4% | +0.2 (+0.3) | 46.8% ±0.7 | 47.6% | -0.8 (-0.9) | -0.001 ±0.001 | -0.003 ±0.004 | 0/5 | no | FAIL |
| b3_touch long, 2m bars | 8049 | 1197 | 52.9% ±0.6 | 53.0% | -0.1 (-0.1) | 53.5% ±0.8 | 53.5% | +0.0 (+0.0) | +0.003 ±0.002 | +0.006 ±0.004 | 1/5 | no | FAIL |
| b3_touch short, 2m bars | 9065 | 1207 | 48.4% ±0.6 | 47.9% | +0.5 (+0.7) | 46.7% ±0.8 | 47.0% | -0.2 (-0.2) | -0.001 ±0.002 | -0.003 ±0.004 | 0/5 | no | FAIL |
| b3_touch long, 3m bars | 6449 | 1105 | 52.7% ±0.7 | 52.1% | +0.6 (+0.7) | 53.6% ±0.9 | 52.0% | +1.6 (+1.4) | +0.002 ±0.002 | +0.004 ±0.005 | 2/5 | no | FAIL |
| b3_touch short, 3m bars | 7322 | 1147 | 48.0% ±0.7 | 47.4% | +0.6 (+0.6) | 46.9% ±0.9 | 46.5% | +0.4 (+0.4) | -0.002 ±0.002 | -0.005 ±0.004 | 1/5 | no | FAIL |
| b3_touch long, 4m bars | 4440 | 1023 | 53.4% ±0.8 | 51.4% | +2.0 (+1.9) | 53.6% ±1.0 | 53.2% | +0.4 (+0.3) | +0.003 ±0.003 | +0.005 ±0.006 | 2/5 | no | FAIL |
| b3_touch short, 4m bars | 5078 | 1069 | 47.4% ±0.8 | 47.3% | +0.1 (+0.1) | 46.9% ±1.0 | 47.0% | -0.1 (-0.1) | -0.004 ±0.002 | -0.008 ±0.005 | 0/5 | no | FAIL |
| b3_touch long, 5m bars | 3567 | 949 | 51.5% ±0.8 | 52.4% | -0.9 (-0.7) | 53.0% ±1.1 | 51.7% | +1.3 (+0.9) | -0.000 ±0.003 | +0.002 ±0.007 | 2/5 | no | FAIL |
| b3_touch short, 5m bars | 4069 | 994 | 48.1% ±0.8 | 47.7% | +0.4 (+0.4) | 47.0% ±1.1 | 46.5% | +0.5 (+0.4) | -0.003 ±0.002 | -0.007 ±0.005 | 1/5 | no | FAIL |
| b3_reentry long, 1m bars | 3724 | 1176 | 53.4% ±0.8 | 53.2% | +0.1 (+0.1) | 53.9% ±0.9 | 53.3% | +0.6 (+0.5) | +0.006 ±0.003 | +0.010 ±0.006 | 2/5 | no | FAIL |
| b3_reentry short, 1m bars | 3599 | 1184 | 47.8% ±0.8 | 48.7% | -1.0 (-0.8) | 46.3% ±0.9 | 47.1% | -0.8 (-0.7) | -0.001 ±0.003 | -0.003 ±0.005 | 0/5 | no | FAIL |
| b3_reentry long, 2m bars | 2127 | 1021 | 52.8% ±1.1 | 51.2% | +1.6 (+1.0) | 52.1% ±1.2 | 53.5% | -1.4 (-0.8) | -0.001 ±0.004 | +0.003 ±0.007 | 1/5 | no | FAIL |
| b3_reentry short, 2m bars | 2044 | 1026 | 48.2% ±1.1 | 50.3% | -2.1 (-1.3) | 46.0% ±1.2 | 48.1% | -2.1 (-1.3) | -0.001 ±0.003 | -0.006 ±0.006 | 0/5 | no | FAIL |
| b3_reentry long, 3m bars | 1510 | 866 | 49.9% ±1.3 | 50.2% | -0.3 (-0.1) | 52.1% ±1.4 | 50.6% | +1.5 (+0.8) | -0.004 ±0.004 | -0.001 ±0.008 | 2/5 | no | FAIL |
| b3_reentry short, 3m bars | 1489 | 884 | 46.6% ±1.4 | 49.8% | -3.2 (-1.7) | 45.4% ±1.4 | 46.9% | -1.5 (-0.8) | -0.003 ±0.004 | -0.011 ±0.008 | 0/5 | no | FAIL |
| b3_reentry long, 4m bars | 1126 | 753 | 51.0% ±1.5 | 51.8% | -0.8 (-0.4) | 52.9% ±1.6 | 52.3% | +0.6 (+0.3) | -0.003 ±0.006 | +0.007 ±0.010 | 0/5 | no | FAIL |
| b3_reentry short, 4m bars | 1120 | 775 | 46.2% ±1.5 | 47.9% | -1.8 (-0.8) | 46.5% ±1.6 | 48.1% | -1.6 (-0.7) | -0.006 ±0.005 | -0.007 ±0.009 | 0/5 | no | FAIL |
| b3_reentry long, 5m bars | 992 | 721 | 50.9% ±1.6 | 52.6% | -1.7 (-0.8) | 53.3% ±1.7 | 51.7% | +1.6 (+0.7) | -0.006 ±0.007 | +0.008 ±0.011 | 0/5 | no | FAIL |
| b3_reentry short, 5m bars | 1028 | 748 | 45.6% ±1.6 | 47.8% | -2.1 (-1.0) | 47.6% ±1.6 | 48.1% | -0.5 (-0.2) | -0.003 ±0.005 | -0.003 ±0.009 | 0/5 | no | FAIL |
| orb15 long, 1m bars | 455 | 455 | 51.6% ±2.3 | 54.5% | -2.9 (-0.9) | 58.7% ±2.3 | 53.6% | +5.1 (+1.6) | +0.011 ±0.008 | +0.029 ±0.012 | 2/5 | no | FAIL |
| orb15 short, 1m bars | 442 | 442 | 47.1% ±2.4 | 48.6% | -1.6 (-0.5) | 48.2% ±2.4 | 43.9% | +4.3 (+1.3) | -0.019 ±0.010 | +0.000 ±0.015 | 1/5 | no | FAIL |
| orb15 long, 5m bars | 101 | 101 | 51.5% ±5.0 | 57.4% | -5.9 (-0.8) | 57.4% ±4.9 | 63.4% | -5.9 (-0.9) | +0.010 ±0.021 | +0.027 ±0.022 | 0/5 | no | FAIL |
| orb15 short, 5m bars | 144 | 144 | 53.5% ±4.2 | 53.5% | +0.0 (+0.0) | 52.8% ±4.2 | 45.8% | +6.9 (+1.2) | +0.009 ±0.018 | +0.026 ±0.030 | 1/5 | no | FAIL |
| orb30 long, 1m bars | 420 | 420 | 50.2% ±2.4 | 51.7% | -1.4 (-0.4) | 56.7% ±2.4 | 53.6% | +3.1 (+0.9) | +0.004 ±0.008 | +0.026 ±0.012 | 3/5 | no | FAIL |
| orb30 short, 1m bars | 426 | 426 | 44.8% ±2.4 | 50.7% | -5.9 (-1.7) | 46.9% ±2.4 | 46.9% | +0.0 (+0.0) | -0.010 ±0.008 | +0.006 ±0.013 | 2/5 | no | FAIL |
| orb30 long, 5m bars | 118 | 118 | 58.5% ±4.6 | 59.3% | -0.8 (-0.1) | 59.3% ±4.5 | 52.5% | +6.8 (+1.1) | +0.001 ±0.014 | +0.023 ±0.019 | 1/5 | no | FAIL |
| orb30 short, 5m bars | 154 | 154 | 53.9% ±4.0 | 51.9% | +1.9 (+0.4) | 47.4% ±4.0 | 46.8% | +0.6 (+0.1) | +0.013 ±0.015 | +0.020 ±0.025 | 0/5 | no | FAIL |
| gap0.5_cont long | 237 | 237 | 49.4% ±3.3 | 48.9% | +0.4 (+0.1) | 53.2% ±3.2 | 50.6% | +2.5 (+0.5) | -0.021 ±0.019 | +0.019 ±0.027 | 2/5 | no | FAIL |
| gap0.5_cont short | 206 | 206 | 56.8% ±3.5 | 46.1% | +10.7 (+2.1) | 61.7% ±3.4 | 51.0% | +10.7 (+2.3) | +0.041 ±0.016 | +0.090 ±0.031 | 3/5 | no | FAIL |
| gap0.5_fill long | 206 | 206 | 41.7% ±3.4 | 49.0% | -7.3 (-1.5) | 38.3% ±3.4 | 52.4% | -14.1 (-3.0) | -0.041 ±0.016 | -0.090 ±0.031 | 0/5 | no | FAIL |
| gap0.5_fill short | 237 | 237 | 50.2% ±3.3 | 41.4% | +8.9 (+1.9) | 46.8% ±3.2 | 45.6% | +1.3 (+0.3) | +0.021 ±0.019 | -0.019 ±0.027 | 1/5 | no | FAIL |
| gap1_cont long | 70 | 70 | 54.3% ±6.0 | 42.9% | +11.4 (+1.4) | 62.9% ±5.8 | 50.0% | +12.9 (+1.5) | -0.022 ±0.049 | +0.108 ±0.064 | 0/5 | no | FAIL |
| gap1_cont short | 83 | 83 | 53.0% ±5.5 | 47.0% | +6.0 (+0.7) | 66.3% ±5.2 | 41.0% | +25.3 (+3.6) | +0.044 ±0.026 | +0.111 ±0.061 | 2/5 | no | FAIL |
| gap1_fill long | 83 | 83 | 44.6% ±5.5 | 55.4% | -10.8 (-1.5) | 33.7% ±5.2 | 47.0% | -13.3 (-1.8) | -0.044 ±0.026 | -0.111 ±0.061 | 0/5 | no | FAIL |
| gap1_fill short | 70 | 70 | 44.3% ±6.0 | 48.6% | -4.3 (-0.5) | 37.1% ±5.8 | 45.7% | -8.6 (-0.9) | +0.022 ±0.049 | -0.108 ±0.064 | 0/5 | no | FAIL |
| first_half_hour long | 178 | 178 | 53.9% ±3.7 | 47.8% | +6.2 (+1.2) | 56.2% ±3.7 | 50.6% | +5.6 (+1.1) | +0.009 ±0.020 | +0.020 ±0.027 | 2/5 | no | FAIL |
| first_half_hour short | 162 | 162 | 51.9% ±3.9 | 45.1% | +6.8 (+1.2) | 45.1% ±3.9 | 54.3% | -9.3 (-1.7) | +0.002 ±0.021 | -0.051 ±0.036 | 1/5 | no | FAIL |

Gap and first-half-hour rules at their extra horizons (control over the same number of minutes):

| Rule | Count | +5m: our way (ctrl), avg % | to 10:00: our way (ctrl), avg % | to 10:30: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|---|---|
| gap0.5_cont long | 237 | 48.1% (53.2%, z -1.1), -0.025 ±0.014 | 52.3% (51.9%, z +0.1), -0.012 ±0.026 | 54.9% (55.7%, z -0.2), +0.032 ±0.032 | 56.5% (54.9%, z +0.4), +0.045 ±0.033 | 57.4% (54.9%, z +0.5), +0.062 ±0.050 |
| gap0.5_cont short | 206 | 47.1% (47.1%, z +0.0), +0.003 ±0.013 | 55.8% (50.0%, z +1.2), +0.021 ±0.028 | 51.9% (42.7%, z +1.9), +0.033 ±0.039 | 55.3% (46.1%, z +1.9), +0.028 ±0.044 | 51.9% (49.5%, z +0.5), +0.023 ±0.061 |
| gap0.5_fill long | 206 | 51.0% (53.4%, z -0.5), -0.003 ±0.013 | 44.2% (52.9%, z -1.8), -0.021 ±0.028 | 48.1% (59.2%, z -2.3), -0.033 ±0.039 | 44.7% (59.2%, z -3.0), -0.028 ±0.044 | 48.1% (55.8%, z -1.6), -0.023 ±0.061 |
| gap0.5_fill short | 237 | 51.1% (44.7%, z +1.4), +0.025 ±0.014 | 47.3% (45.1%, z +0.4), +0.012 ±0.026 | 45.1% (43.9%, z +0.3), -0.032 ±0.032 | 43.5% (48.1%, z -1.0), -0.045 ±0.033 | 42.2% (44.3%, z -0.5), -0.062 ±0.050 |
| gap1_cont long | 70 | 50.0% (47.1%, z +0.3), -0.045 ±0.032 | 60.0% (51.4%, z +1.0), +0.045 ±0.068 | 58.6% (62.9%, z -0.5), +0.159 ±0.073 | 60.0% (58.6%, z +0.2), +0.155 ±0.076 | 64.3% (60.0%, z +0.5), +0.145 ±0.128 |
| gap1_cont short | 83 | 44.6% (48.2%, z -0.5), -0.017 ±0.025 | 54.2% (43.4%, z +1.4), -0.032 ±0.055 | 57.8% (44.6%, z +1.9), +0.064 ±0.073 | 60.2% (48.2%, z +1.7), +0.024 ±0.084 | 55.4% (45.8%, z +1.2), -0.013 ±0.121 |
| gap1_fill long | 83 | 51.8% (55.4%, z -0.4), +0.017 ±0.025 | 45.8% (51.8%, z -0.8), +0.032 ±0.055 | 42.2% (53.0%, z -1.4), -0.064 ±0.073 | 39.8% (51.8%, z -1.6), -0.024 ±0.084 | 44.6% (49.4%, z -0.6), +0.013 ±0.121 |
| gap1_fill short | 70 | 50.0% (52.9%, z -0.3), +0.045 ±0.032 | 38.6% (47.1%, z -1.0), -0.045 ±0.068 | 41.4% (37.1%, z +0.5), -0.159 ±0.073 | 40.0% (40.0%, z +0.0), -0.155 ±0.076 | 35.7% (38.6%, z -0.4), -0.145 ±0.128 |

| Rule | Count | +5m: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|
| first_half_hour long | 178 | 51.7% (42.7%, z +1.8), -0.007 ±0.017 | 56.7% (52.2%, z +0.8), +0.057 ±0.036 | 57.9% (52.2%, z +1.1), +0.106 ±0.051 |
| first_half_hour short | 162 | 51.9% (54.9%, z -0.6), +0.021 ±0.017 | 48.8% (53.1%, z -0.8), -0.023 ±0.048 | 48.8% (45.7%, z +0.5), -0.033 ±0.069 |

## atr_pick: the ATR % pick (comparison with earlier tests)

| Rule | Count | Days | Our way 10m | Ctrl 10m | Gap 10m (z) | Our way 30m | Ctrl 30m | Gap 30m (z) | Avg 10m % | Avg 30m % | Years held | Meets bar | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 281 | 247 | 49.5% ±2.9 | 49.1% | +0.4 (+0.1) | 48.0% ±3.0 | 54.1% | -6.0 (-1.4) | +0.022 ±0.021 | -0.028 ±0.037 | 1/5 | no | (comparison only) |
| squeeze short, 1m bars | 267 | 245 | 50.2% ±3.0 | 48.3% | +1.9 (+0.4) | 47.9% ±3.0 | 46.1% | +1.9 (+0.4) | +0.053 ±0.032 | +0.088 ±0.047 | 2/5 | no | (comparison only) |
| squeeze long, 2m bars | 94 | 89 | 57.4% ±4.8 | 45.7% | +11.7 (+1.7) | 59.6% ±5.1 | 46.8% | +12.8 (+1.8) | +0.078 ±0.039 | +0.188 ±0.091 | 3/5 | no | (comparison only) |
| squeeze short, 2m bars | 91 | 85 | 48.4% ±5.3 | 44.0% | +4.4 (+0.6) | 44.0% ±5.4 | 44.0% | +0.0 (+0.0) | +0.041 ±0.035 | +0.088 ±0.079 | 2/5 | no | (comparison only) |
| squeeze long, 3m bars | 70 | 66 | 58.6% ±5.9 | 41.4% | +17.1 (+1.9) | 58.6% ±6.2 | 55.7% | +2.9 (+0.3) | +0.130 ±0.062 | +0.164 ±0.122 | 3/5 | no | (comparison only) |
| squeeze short, 3m bars | 78 | 74 | 56.4% ±5.9 | 59.0% | -2.6 (-0.3) | 55.1% ±5.8 | 55.1% | +0.0 (+0.0) | -0.051 ±0.098 | +0.032 ±0.111 | 2/5 | no | (comparison only) |
| squeeze long, 4m bars | 80 | 76 | 46.2% ±5.7 | 47.5% | -1.2 (-0.2) | 43.8% ±5.6 | 40.0% | +3.8 (+0.5) | -0.015 ±0.077 | -0.054 ±0.106 | 2/5 | no | (comparison only) |
| squeeze short, 4m bars | 66 | 65 | 51.5% ±6.3 | 43.9% | +7.6 (+0.8) | 57.6% ±6.2 | 47.0% | +10.6 (+1.2) | -0.122 ±0.105 | +0.155 ±0.144 | 2/5 | no | (comparison only) |
| squeeze long, 5m bars | 90 | 83 | 50.0% ±5.1 | 48.9% | +1.1 (+0.2) | 46.7% ±5.6 | 46.7% | +0.0 (+0.0) | +0.047 ±0.073 | +0.018 ±0.114 | 2/5 | no | (comparison only) |
| squeeze short, 5m bars | 92 | 88 | 48.9% ±5.4 | 48.9% | +0.0 (+0.0) | 46.7% ±5.4 | 41.3% | +5.4 (+0.7) | +0.016 ±0.081 | +0.132 ±0.142 | 0/5 | no | (comparison only) |
| pullback long, 1m bars | 355 | 298 | 51.0% ±2.6 | 51.5% | -0.6 (-0.2) | 53.5% ±2.7 | 49.3% | +4.2 (+1.2) | +0.027 ±0.024 | +0.059 ±0.039 | 2/5 | no | (comparison only) |
| pullback short, 1m bars | 262 | 229 | 51.9% ±3.1 | 50.0% | +1.9 (+0.4) | 51.9% ±3.2 | 44.3% | +7.6 (+1.6) | +0.031 ±0.023 | +0.062 ±0.038 | 2/5 | no | (comparison only) |
| pullback long, 2m bars | 134 | 124 | 50.7% ±4.3 | 51.5% | -0.7 (-0.1) | 51.5% ±4.4 | 51.5% | +0.0 (+0.0) | +0.034 ±0.036 | +0.018 ±0.067 | 1/5 | no | (comparison only) |
| pullback short, 2m bars | 102 | 100 | 44.1% ±5.0 | 50.0% | -5.9 (-0.8) | 48.0% ±5.1 | 56.9% | -8.8 (-1.3) | -0.014 ±0.052 | +0.053 ±0.064 | 0/5 | no | (comparison only) |
| pullback long, 3m bars | 82 | 80 | 50.0% ±5.6 | 45.1% | +4.9 (+0.6) | 53.7% ±5.7 | 45.1% | +8.5 (+1.0) | +0.090 ±0.064 | +0.018 ±0.105 | 2/5 | no | (comparison only) |
| pullback short, 3m bars | 72 | 70 | 54.2% ±5.9 | 47.2% | +6.9 (+0.8) | 50.0% ±6.1 | 56.9% | -6.9 (-0.8) | -0.032 ±0.068 | +0.012 ±0.120 | 1/5 | no | (comparison only) |
| pullback long, 4m bars | 55 | 52 | 50.9% ±6.8 | 54.5% | -3.6 (-0.4) | 50.9% ±6.5 | 41.8% | +9.1 (+1.0) | +0.007 ±0.098 | +0.069 ±0.127 | 1/5 | no | (comparison only) |
| pullback short, 4m bars | 70 | 68 | 58.6% ±6.0 | 51.4% | +7.1 (+0.8) | 62.9% ±6.0 | 58.6% | +4.3 (+0.5) | +0.219 ±0.073 | +0.367 ±0.123 | 3/5 | no | (comparison only) |
| pullback long, 5m bars | 60 | 56 | 50.0% ±6.3 | 46.7% | +3.3 (+0.4) | 53.3% ±6.9 | 53.3% | +0.0 (+0.0) | -0.017 ±0.090 | -0.000 ±0.133 | 1/5 | no | (comparison only) |
| pullback short, 5m bars | 73 | 67 | 58.9% ±5.9 | 54.8% | +4.1 (+0.6) | 56.2% ±5.9 | 60.3% | -4.1 (-0.5) | +0.127 ±0.061 | +0.256 ±0.152 | 0/5 | no | (comparison only) |
| e1_trend long, 1m bars | 6273 | 1217 | 51.1% ±0.6 | 50.0% | +1.1 (+1.3) | 51.2% ±0.8 | 51.0% | +0.2 (+0.2) | +0.008 ±0.005 | +0.020 ±0.012 | 2/5 | no | (comparison only) |
| e1_trend short, 1m bars | 6086 | 1214 | 49.5% ±0.7 | 48.0% | +1.5 (+1.6) | 49.3% ±0.8 | 46.6% | +2.7 (+2.5) | +0.007 ±0.006 | +0.014 ±0.012 | 2/5 | no | (comparison only) |
| e1_trend long, 2m bars | 3093 | 1150 | 49.4% ±0.9 | 49.8% | -0.4 (-0.3) | 49.7% ±1.0 | 50.1% | -0.4 (-0.3) | +0.001 ±0.007 | +0.007 ±0.014 | 0/5 | no | (comparison only) |
| e1_trend short, 2m bars | 2997 | 1130 | 49.7% ±0.9 | 47.3% | +2.4 (+1.9) | 48.5% ±1.0 | 47.4% | +1.0 (+0.8) | -0.001 ±0.008 | +0.004 ±0.016 | 2/5 | no | (comparison only) |
| e1_trend long, 3m bars | 2001 | 1019 | 50.2% ±1.1 | 49.5% | +0.7 (+0.4) | 49.8% ±1.2 | 50.5% | -0.7 (-0.4) | +0.002 ±0.009 | +0.002 ±0.016 | 0/5 | no | (comparison only) |
| e1_trend short, 3m bars | 1934 | 996 | 48.2% ±1.2 | 49.0% | -0.7 (-0.5) | 49.0% ±1.2 | 50.1% | -1.1 (-0.7) | -0.002 ±0.010 | -0.001 ±0.020 | 0/5 | no | (comparison only) |
| e1_trend long, 4m bars | 1455 | 900 | 50.9% ±1.3 | 50.0% | +0.9 (+0.5) | 49.2% ±1.3 | 50.1% | -0.9 (-0.5) | +0.001 ±0.010 | -0.012 ±0.020 | 0/5 | no | (comparison only) |
| e1_trend short, 4m bars | 1417 | 855 | 49.4% ±1.3 | 47.1% | +2.3 (+1.2) | 47.8% ±1.4 | 47.8% | +0.0 (+0.0) | +0.018 ±0.013 | -0.000 ±0.022 | 2/5 | no | (comparison only) |
| e1_trend long, 5m bars | 1323 | 842 | 50.6% ±1.3 | 49.7% | +0.9 (+0.5) | 50.3% ±1.5 | 51.1% | -0.8 (-0.4) | +0.000 ±0.014 | -0.000 ±0.022 | 1/5 | no | (comparison only) |
| e1_trend short, 5m bars | 1315 | 816 | 48.7% ±1.4 | 48.6% | +0.1 (+0.0) | 49.0% ±1.4 | 49.4% | -0.3 (-0.2) | -0.000 ±0.014 | -0.008 ±0.024 | 1/5 | no | (comparison only) |
| e1_reject long, 1m bars | 10044 | 1215 | 50.3% ±0.5 | 50.0% | +0.3 (+0.4) | 51.3% ±0.7 | 50.5% | +0.8 (+0.9) | +0.010 ±0.005 | +0.025 ±0.011 | 2/5 | no | (comparison only) |
| e1_reject short, 1m bars | 9265 | 1213 | 49.0% ±0.6 | 48.2% | +0.8 (+1.1) | 49.5% ±0.7 | 47.8% | +1.7 (+1.9) | +0.007 ±0.005 | +0.016 ±0.012 | 1/5 | no | (comparison only) |
| e1_reject long, 2m bars | 6930 | 1143 | 49.8% ±0.7 | 50.1% | -0.2 (-0.3) | 50.8% ±0.9 | 51.3% | -0.5 (-0.5) | +0.007 ±0.006 | +0.024 ±0.012 | 0/5 | no | (comparison only) |
| e1_reject short, 2m bars | 6038 | 1105 | 49.4% ±0.7 | 48.3% | +1.1 (+1.2) | 49.1% ±0.9 | 48.0% | +1.1 (+1.0) | +0.015 ±0.006 | +0.018 ±0.013 | 3/5 | no | (comparison only) |
| e1_reject long, 3m bars | 5146 | 1030 | 50.5% ±0.7 | 50.2% | +0.4 (+0.4) | 50.6% ±1.0 | 51.3% | -0.8 (-0.6) | +0.004 ±0.006 | +0.016 ±0.013 | 3/5 | no | (comparison only) |
| e1_reject short, 3m bars | 4562 | 976 | 48.3% ±0.8 | 48.2% | +0.1 (+0.1) | 47.7% ±1.0 | 47.5% | +0.2 (+0.1) | -0.003 ±0.008 | -0.002 ±0.015 | 1/5 | no | (comparison only) |
| e1_reject long, 4m bars | 3804 | 939 | 49.8% ±0.8 | 50.6% | -0.8 (-0.7) | 50.4% ±1.1 | 50.4% | -0.0 (-0.0) | +0.004 ±0.007 | +0.013 ±0.014 | 0/5 | no | (comparison only) |
| e1_reject short, 4m bars | 3261 | 874 | 48.1% ±0.9 | 47.2% | +1.0 (+0.8) | 48.4% ±1.1 | 47.5% | +0.9 (+0.6) | +0.005 ±0.008 | +0.011 ±0.016 | 1/5 | no | (comparison only) |
| e1_reject long, 5m bars | 2921 | 853 | 50.3% ±0.9 | 50.0% | +0.3 (+0.2) | 51.3% ±1.1 | 49.6% | +1.7 (+1.2) | +0.003 ±0.008 | +0.025 ±0.015 | 3/5 | no | (comparison only) |
| e1_reject short, 5m bars | 2562 | 794 | 49.6% ±1.0 | 49.0% | +0.7 (+0.5) | 48.9% ±1.1 | 46.9% | +2.0 (+1.3) | -0.001 ±0.010 | +0.016 ±0.019 | 1/5 | no | (comparison only) |
| r2_rsi long, 1m bars | 1650 | 801 | 51.1% ±1.2 | 49.6% | +1.5 (+0.9) | 51.0% ±1.4 | 50.2% | +0.8 (+0.4) | -0.019 ±0.015 | -0.003 ±0.026 | 0/5 | no | (comparison only) |
| r2_rsi short, 1m bars | 1036 | 626 | 47.6% ±1.5 | 50.5% | -2.9 (-1.3) | 46.8% ±1.7 | 49.4% | -2.6 (-1.1) | -0.026 ±0.014 | -0.035 ±0.025 | 1/5 | no | (comparison only) |
| r2_rsi long, 2m bars | 1066 | 604 | 48.2% ±1.5 | 51.2% | -3.0 (-1.4) | 50.2% ±1.7 | 53.2% | -3.0 (-1.4) | -0.036 ±0.019 | -0.015 ±0.032 | 0/5 | no | (comparison only) |
| r2_rsi short, 2m bars | 655 | 449 | 47.9% ±2.0 | 47.6% | +0.3 (+0.1) | 46.3% ±2.1 | 48.7% | -2.4 (-0.8) | -0.049 ±0.021 | -0.069 ±0.035 | 0/5 | no | (comparison only) |
| r2_rsi long, 3m bars | 901 | 514 | 49.9% ±1.7 | 50.2% | -0.2 (-0.1) | 50.9% ±1.8 | 50.7% | +0.2 (+0.1) | -0.019 ±0.017 | -0.009 ±0.030 | 1/5 | no | (comparison only) |
| r2_rsi short, 3m bars | 498 | 378 | 45.2% ±2.3 | 49.0% | -3.8 (-1.2) | 46.0% ±2.2 | 50.0% | -4.0 (-1.3) | -0.049 ±0.023 | -0.068 ±0.041 | 0/5 | no | (comparison only) |
| r2_rsi long, 4m bars | 738 | 452 | 48.9% ±1.8 | 50.5% | -1.6 (-0.6) | 51.2% ±1.9 | 53.0% | -1.8 (-0.6) | -0.047 ±0.021 | -0.019 ±0.033 | 0/5 | no | (comparison only) |
| r2_rsi short, 4m bars | 421 | 362 | 46.6% ±2.4 | 48.5% | -1.9 (-0.6) | 49.6% ±2.5 | 48.2% | +1.4 (+0.4) | -0.017 ±0.024 | -0.017 ±0.043 | 0/5 | no | (comparison only) |
| r2_rsi long, 5m bars | 656 | 434 | 48.5% ±1.9 | 49.2% | -0.8 (-0.3) | 51.5% ±2.1 | 50.9% | +0.6 (+0.2) | -0.032 ±0.019 | -0.010 ±0.033 | 1/5 | no | (comparison only) |
| r2_rsi short, 5m bars | 370 | 327 | 45.4% ±2.5 | 48.1% | -2.7 (-0.7) | 50.5% ±2.6 | 47.3% | +3.2 (+0.9) | -0.045 ±0.023 | -0.014 ±0.037 | 0/5 | no | (comparison only) |
| r2_rsi_sym long, 1m bars | 918 | 581 | 49.6% ±1.7 | 52.1% | -2.5 (-1.1) | 51.0% ±1.8 | 50.8% | +0.2 (+0.1) | -0.032 ±0.021 | +0.001 ±0.038 | 0/5 | no | (comparison only) |
| r2_rsi_sym short, 1m bars | 1036 | 626 | 47.6% ±1.5 | 49.1% | -1.5 (-0.7) | 46.8% ±1.7 | 46.6% | +0.2 (+0.1) | -0.026 ±0.014 | -0.035 ±0.025 | 2/5 | no | (comparison only) |
| r2_rsi_sym long, 2m bars | 578 | 423 | 49.1% ±2.1 | 49.7% | -0.5 (-0.2) | 51.9% ±2.2 | 55.9% | -4.0 (-1.3) | -0.023 ±0.024 | +0.007 ±0.044 | 1/5 | no | (comparison only) |
| r2_rsi_sym short, 2m bars | 655 | 449 | 47.9% ±2.0 | 47.8% | +0.2 (+0.1) | 46.3% ±2.1 | 47.9% | -1.7 (-0.6) | -0.049 ±0.021 | -0.069 ±0.035 | 0/5 | no | (comparison only) |
| r2_rsi_sym long, 3m bars | 455 | 356 | 48.6% ±2.3 | 53.0% | -4.4 (-1.3) | 53.4% ±2.4 | 50.8% | +2.6 (+0.8) | -0.028 ±0.023 | +0.007 ±0.037 | 0/5 | no | (comparison only) |
| r2_rsi_sym short, 3m bars | 498 | 378 | 45.2% ±2.3 | 48.4% | -3.2 (-1.0) | 46.0% ±2.2 | 48.2% | -2.2 (-0.7) | -0.049 ±0.023 | -0.068 ±0.041 | 0/5 | no | (comparison only) |
| r2_rsi_sym long, 4m bars | 372 | 302 | 50.8% ±2.5 | 49.5% | +1.3 (+0.4) | 51.3% ±2.5 | 54.6% | -3.2 (-0.9) | -0.053 ±0.037 | -0.020 ±0.048 | 0/5 | no | (comparison only) |
| r2_rsi_sym short, 4m bars | 421 | 362 | 46.6% ±2.4 | 45.4% | +1.2 (+0.3) | 49.6% ±2.5 | 45.8% | +3.8 (+1.1) | -0.017 ±0.024 | -0.017 ±0.043 | 0/5 | no | (comparison only) |
| r2_rsi_sym long, 5m bars | 340 | 285 | 50.6% ±2.7 | 49.7% | +0.9 (+0.2) | 54.4% ±2.7 | 50.3% | +4.1 (+1.1) | -0.021 ±0.027 | +0.022 ±0.041 | 0/5 | no | (comparison only) |
| r2_rsi_sym short, 5m bars | 370 | 327 | 45.4% ±2.5 | 48.1% | -2.7 (-0.7) | 50.5% ±2.6 | 47.3% | +3.2 (+0.9) | -0.045 ±0.023 | -0.014 ±0.037 | 0/5 | no | (comparison only) |
| b3_touch long, 1m bars | 9196 | 1217 | 50.0% ±0.5 | 50.3% | -0.3 (-0.5) | 50.6% ±0.7 | 51.2% | -0.6 (-0.7) | -0.000 ±0.005 | -0.006 ±0.010 | 0/5 | no | (comparison only) |
| b3_touch short, 1m bars | 9512 | 1218 | 47.9% ±0.5 | 48.9% | -1.0 (-1.3) | 47.9% ±0.7 | 48.1% | -0.1 (-0.2) | -0.009 ±0.004 | -0.017 ±0.010 | 0/5 | no | (comparison only) |
| b3_touch long, 2m bars | 6313 | 1166 | 50.3% ±0.7 | 50.2% | +0.1 (+0.1) | 51.1% ±0.9 | 51.5% | -0.4 (-0.4) | -0.007 ±0.006 | -0.011 ±0.012 | 0/5 | no | (comparison only) |
| b3_touch short, 2m bars | 6465 | 1182 | 48.6% ±0.7 | 47.6% | +1.0 (+1.1) | 48.5% ±0.9 | 47.2% | +1.3 (+1.2) | -0.013 ±0.006 | -0.019 ±0.012 | 1/5 | no | (comparison only) |
| b3_touch long, 3m bars | 5114 | 1074 | 49.6% ±0.8 | 50.2% | -0.5 (-0.5) | 51.0% ±1.0 | 50.7% | +0.4 (+0.3) | -0.009 ±0.009 | -0.002 ±0.016 | 1/5 | no | (comparison only) |
| b3_touch short, 3m bars | 5341 | 1101 | 47.9% ±0.8 | 47.4% | +0.5 (+0.5) | 47.9% ±1.0 | 47.0% | +0.9 (+0.7) | -0.015 ±0.008 | -0.027 ±0.017 | 1/5 | no | (comparison only) |
| b3_touch long, 4m bars | 3662 | 967 | 49.0% ±0.8 | 51.0% | -2.0 (-1.7) | 49.8% ±1.1 | 52.3% | -2.6 (-1.9) | -0.018 ±0.009 | -0.013 ±0.019 | 0/5 | no | (comparison only) |
| b3_touch short, 4m bars | 3803 | 1009 | 48.9% ±0.9 | 50.4% | -1.5 (-1.3) | 47.9% ±1.1 | 48.9% | -1.0 (-0.8) | -0.007 ±0.009 | -0.023 ±0.018 | 0/5 | no | (comparison only) |
| b3_touch long, 5m bars | 3092 | 888 | 50.5% ±0.9 | 51.1% | -0.6 (-0.5) | 50.3% ±1.1 | 52.2% | -2.0 (-1.4) | -0.001 ±0.010 | -0.004 ±0.021 | 1/5 | no | (comparison only) |
| b3_touch short, 5m bars | 3364 | 951 | 47.5% ±0.9 | 47.9% | -0.4 (-0.4) | 47.2% ±1.1 | 46.9% | +0.3 (+0.2) | -0.018 ±0.009 | -0.041 ±0.020 | 0/5 | no | (comparison only) |
| b3_reentry long, 1m bars | 3803 | 1193 | 50.5% ±0.8 | 50.6% | -0.1 (-0.1) | 50.6% ±0.9 | 52.2% | -1.6 (-1.3) | +0.008 ±0.008 | +0.009 ±0.014 | 0/5 | no | (comparison only) |
| b3_reentry short, 1m bars | 3617 | 1187 | 48.2% ±0.8 | 48.1% | +0.1 (+0.1) | 47.8% ±0.9 | 47.7% | +0.1 (+0.0) | -0.016 ±0.008 | -0.027 ±0.014 | 0/5 | no | (comparison only) |
| b3_reentry long, 2m bars | 2194 | 1036 | 51.3% ±1.1 | 48.3% | +3.0 (+2.0) | 50.3% ±1.1 | 49.8% | +0.5 (+0.3) | -0.013 ±0.012 | -0.011 ±0.019 | 1/5 | no | (comparison only) |
| b3_reentry short, 2m bars | 2136 | 1035 | 49.4% ±1.1 | 48.8% | +0.6 (+0.4) | 47.2% ±1.2 | 48.4% | -1.2 (-0.7) | -0.012 ±0.012 | -0.037 ±0.021 | 0/5 | no | (comparison only) |
| b3_reentry long, 3m bars | 1612 | 873 | 49.5% ±1.3 | 50.7% | -1.2 (-0.7) | 50.4% ±1.4 | 51.4% | -0.9 (-0.5) | -0.020 ±0.014 | -0.015 ±0.025 | 0/5 | no | (comparison only) |
| b3_reentry short, 3m bars | 1565 | 905 | 48.9% ±1.3 | 48.6% | +0.3 (+0.1) | 47.5% ±1.4 | 48.2% | -0.7 (-0.4) | -0.017 ±0.014 | -0.036 ±0.025 | 1/5 | no | (comparison only) |
| b3_reentry long, 4m bars | 1242 | 772 | 49.0% ±1.5 | 50.9% | -1.9 (-0.9) | 48.8% ±1.5 | 51.7% | -2.9 (-1.4) | -0.027 ±0.017 | +0.001 ±0.029 | 0/5 | no | (comparison only) |
| b3_reentry short, 4m bars | 1210 | 805 | 48.0% ±1.4 | 47.4% | +0.7 (+0.3) | 48.2% ±1.5 | 45.8% | +2.4 (+1.2) | -0.018 ±0.015 | -0.018 ±0.026 | 1/5 | no | (comparison only) |
| b3_reentry long, 5m bars | 1112 | 734 | 47.6% ±1.5 | 50.8% | -3.2 (-1.5) | 52.1% ±1.5 | 51.9% | +0.2 (+0.1) | -0.047 ±0.017 | +0.009 ±0.027 | 1/5 | no | (comparison only) |
| b3_reentry short, 5m bars | 1126 | 785 | 47.7% ±1.5 | 48.2% | -0.5 (-0.2) | 48.3% ±1.6 | 50.8% | -2.5 (-1.1) | -0.003 ±0.016 | -0.014 ±0.027 | 1/5 | no | (comparison only) |
| orb15 long, 1m bars | 287 | 287 | 51.9% ±3.0 | 52.6% | -0.7 (-0.2) | 56.4% ±2.9 | 49.8% | +6.6 (+1.5) | +0.051 ±0.029 | +0.094 ±0.045 | 2/5 | no | (comparison only) |
| orb15 short, 1m bars | 276 | 276 | 51.4% ±3.0 | 49.6% | +1.8 (+0.4) | 52.5% ±3.0 | 48.2% | +4.3 (+1.1) | +0.058 ±0.034 | +0.046 ±0.044 | 1/5 | no | (comparison only) |
| orb15 long, 5m bars | 44 | 44 | 59.1% ±7.5 | 45.5% | +13.6 (+1.2) | 54.5% ±7.6 | 52.3% | +2.3 (+0.2) | +0.007 ±0.068 | +0.044 ±0.093 | 1/5 | no | (comparison only) |
| orb15 short, 5m bars | 57 | 57 | 50.9% ±6.7 | 45.6% | +5.3 (+0.6) | 45.6% ±6.7 | 49.1% | -3.5 (-0.4) | +0.015 ±0.110 | +0.053 ±0.145 | 2/5 | no | (comparison only) |
| orb30 long, 1m bars | 285 | 285 | 53.3% ±3.0 | 48.8% | +4.6 (+1.1) | 55.4% ±2.9 | 49.8% | +5.6 (+1.3) | +0.009 ±0.028 | +0.076 ±0.043 | 1/5 | no | (comparison only) |
| orb30 short, 1m bars | 288 | 288 | 50.7% ±3.0 | 49.7% | +1.0 (+0.3) | 50.3% ±3.0 | 47.9% | +2.4 (+0.6) | +0.044 ±0.028 | +0.052 ±0.035 | 1/5 | no | (comparison only) |
| orb30 long, 5m bars | 51 | 51 | 47.1% ±7.1 | 51.0% | -3.9 (-0.4) | 47.1% ±7.1 | 49.0% | -2.0 (-0.2) | -0.055 ±0.053 | +0.033 ±0.072 | 1/5 | no | (comparison only) |
| orb30 short, 5m bars | 69 | 69 | 49.3% ±6.1 | 50.7% | -1.4 (-0.2) | 44.9% ±6.0 | 49.3% | -4.3 (-0.5) | -0.073 ±0.063 | -0.051 ±0.086 | 0/5 | no | (comparison only) |
| gap0.5_cont long | 440 | 440 | 49.3% ±2.4 | 50.0% | -0.7 (-0.2) | 53.0% ±2.4 | 51.4% | +1.6 (+0.5) | +0.014 ±0.040 | +0.048 ±0.066 | 1/5 | no | (comparison only) |
| gap0.5_cont short | 334 | 334 | 52.4% ±2.7 | 43.1% | +9.3 (+2.4) | 54.8% ±2.7 | 50.6% | +4.2 (+1.1) | +0.072 ±0.047 | +0.086 ±0.072 | 1/5 | no | (comparison only) |
| gap0.5_fill long | 334 | 334 | 45.5% ±2.7 | 44.6% | +0.9 (+0.2) | 44.0% ±2.7 | 47.3% | -3.3 (-0.8) | -0.072 ±0.047 | -0.086 ±0.072 | 0/5 | no | (comparison only) |
| gap0.5_fill short | 440 | 440 | 50.0% ±2.4 | 47.5% | +2.5 (+0.7) | 47.0% ±2.4 | 47.5% | -0.5 (-0.1) | -0.014 ±0.040 | -0.048 ±0.066 | 1/5 | no | (comparison only) |
| gap1_cont long | 277 | 277 | 52.7% ±3.0 | 45.5% | +7.2 (+1.8) | 56.3% ±3.0 | 51.6% | +4.7 (+1.1) | +0.071 ±0.055 | +0.171 ±0.093 | 3/5 | no | (comparison only) |
| gap1_cont short | 223 | 223 | 53.8% ±3.3 | 53.4% | +0.4 (+0.1) | 53.8% ±3.3 | 49.3% | +4.5 (+1.0) | +0.100 ±0.064 | +0.095 ±0.097 | 0/5 | no | (comparison only) |
| gap1_fill long | 223 | 223 | 43.9% ±3.3 | 49.8% | -5.8 (-1.2) | 45.3% ±3.3 | 46.6% | -1.3 (-0.3) | -0.100 ±0.064 | -0.095 ±0.097 | 0/5 | no | (comparison only) |
| gap1_fill short | 277 | 277 | 46.6% ±3.0 | 46.2% | +0.4 (+0.1) | 43.7% ±3.0 | 43.7% | +0.0 (+0.0) | -0.071 ±0.055 | -0.171 ±0.093 | 0/5 | no | (comparison only) |
| first_half_hour long | 428 | 428 | 52.3% ±2.4 | 48.6% | +3.7 (+1.0) | 54.9% ±2.4 | 48.6% | +6.3 (+1.8) | +0.028 ±0.027 | +0.062 ±0.041 | 3/5 | no | (comparison only) |
| first_half_hour short | 410 | 410 | 52.7% ±2.5 | 53.2% | -0.5 (-0.1) | 51.7% ±2.5 | 51.7% | +0.0 (+0.0) | +0.036 ±0.031 | +0.012 ±0.050 | 1/5 | no | (comparison only) |

Gap and first-half-hour rules at their extra horizons (control over the same number of minutes):

| Rule | Count | +5m: our way (ctrl), avg % | to 10:00: our way (ctrl), avg % | to 10:30: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|---|---|
| gap0.5_cont long | 440 | 46.4% (50.9%, z -1.3), -0.013 ±0.033 | 53.4% (50.5%, z +0.9), +0.041 ±0.061 | 50.2% (48.9%, z +0.4), +0.015 ±0.074 | 50.2% (48.6%, z +0.5), +0.047 ±0.078 | 50.0% (46.1%, z +1.2), +0.045 ±0.098 |
| gap0.5_cont short | 334 | 47.9% (46.7%, z +0.3), +0.005 ±0.036 | 51.5% (50.6%, z +0.2), +0.030 ±0.065 | 50.9% (51.2%, z -0.1), -0.042 ±0.087 | 51.8% (48.5%, z +0.8), -0.021 ±0.093 | 54.2% (50.6%, z +0.9), -0.015 ±0.111 |
| gap0.5_fill long | 334 | 50.6% (43.4%, z +1.8), -0.005 ±0.036 | 47.6% (47.9%, z -0.1), -0.030 ±0.065 | 48.8% (52.1%, z -0.9), +0.042 ±0.087 | 47.9% (50.3%, z -0.6), +0.021 ±0.093 | 45.8% (47.0%, z -0.3), +0.015 ±0.111 |
| gap0.5_fill short | 440 | 53.2% (48.9%, z +1.3), +0.013 ±0.033 | 46.4% (46.1%, z +0.1), -0.041 ±0.061 | 49.8% (48.9%, z +0.3), -0.015 ±0.074 | 49.8% (49.1%, z +0.2), -0.047 ±0.078 | 50.0% (46.6%, z +1.0), -0.045 ±0.098 |
| gap1_cont long | 277 | 49.5% (46.2%, z +0.8), +0.044 ±0.045 | 57.0% (49.8%, z +1.7), +0.157 ±0.084 | 50.9% (48.7%, z +0.5), +0.096 ±0.102 | 51.3% (48.0%, z +0.8), +0.140 ±0.105 | 51.6% (47.3%, z +1.0), +0.146 ±0.134 |
| gap1_cont short | 223 | 50.2% (47.5%, z +0.6), +0.005 ±0.048 | 51.1% (54.3%, z -0.7), +0.044 ±0.089 | 48.9% (51.1%, z -0.5), -0.091 ±0.117 | 48.0% (52.9%, z -1.0), -0.074 ±0.126 | 54.3% (46.2%, z +1.7), -0.054 ±0.146 |
| gap1_fill long | 223 | 48.4% (55.2%, z -1.4), -0.005 ±0.048 | 47.5% (46.2%, z +0.3), -0.044 ±0.089 | 50.7% (48.4%, z +0.5), +0.091 ±0.117 | 51.6% (47.5%, z +0.8), +0.074 ±0.126 | 45.7% (48.4%, z -0.6), +0.054 ±0.146 |
| gap1_fill short | 277 | 50.5% (46.9%, z +0.9), -0.044 ±0.045 | 42.6% (43.0%, z -0.1), -0.157 ±0.084 | 49.1% (43.7%, z +1.3), -0.096 ±0.102 | 48.7% (43.7%, z +1.2), -0.140 ±0.105 | 48.4% (47.3%, z +0.3), -0.146 ±0.134 |

| Rule | Count | +5m: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|
| first_half_hour long | 428 | 51.2% (51.6%, z -0.1), +0.038 ±0.020 | 54.7% (49.3%, z +1.5), +0.111 ±0.055 | 54.2% (50.9%, z +0.9), +0.154 ±0.070 |
| first_half_hour short | 410 | 52.0% (50.7%, z +0.3), +0.062 ±0.024 | 50.2% (48.8%, z +0.4), +0.051 ±0.070 | 50.5% (47.6%, z +0.9), +0.044 ±0.083 |

The year-by-year tables for every row are in the full report.

---

Full per-trade tables: [history/2026-10-28-t10b-corrected-control.md](history/2026-10-28-t10b-corrected-control.md)
