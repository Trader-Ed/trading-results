# T11: breakout box, intraday Keltner and daily Keltner filter (2019-2023)

**Comparisons: 82 rule × side × bar-size candidates, each judged in all9 and spy (162 rows, 324 tests of the 3-standard-error bar at 10 and 30 minutes).** If no rule had any edge, a single test clears 3 standard errors one time in about 740, so about 0.4 of the 324 tests would clear it by chance, and a full PASS (both horizons, 4 of 5 years, both universes) would almost never happen by chance (well under 0.1 expected).

## Findings

**PASS: none.** No rule × side × bar size meets the pass bar in both all9 and spy.

**The 10 strongest results** (all9 and spy rows, ranked by the smaller of the 10- and 30-minute z):

| # | Rule | Universe | Count | Gap 10m (z) | Gap 30m (z) | Avg 30m % | Years held | Year by year: gap 30m (pts) |
|---|---|---|---|---|---|---|---|---|
| 1 | kc_mom_p6_m2 long, 15m bars | all9 | 4150 | +2.9 (+2.1) | +3.8 (+2.3) | +0.054 | 4/5 | 2019: +1.4✓, 2020: +0.1, 2021: +14.5✓, 2022: +0.9✓, 2023: +1.0✓ |
| 2 | kc_mom_p6_m2 long, 5m bars | all9 | 4348 | +2.9 (+2.1) | +5.3 (+3.4) | +0.077 | 5/5 | 2019: +5.6✓, 2020: +2.9✓, 2021: +7.6✓, 2022: +9.7✓, 2023: +1.8✓ |
| 3 | kc_mom_p20_m2 long, 15m bars | all9 | 22420 | +1.9 (+2.7) | +1.6 (+1.9) | +0.024 | 4/5 | 2019: +0.4✓, 2020: +0.7✓, 2021: +4.6✓, 2022: +3.6✓, 2023: -1.2 |
| 4 | box_k0.15_c0 long, 15m bars | all9 | 57 | +21.1 (+2.4) | +14.0 (+1.6) | +0.068 | 2/5 | 2019: +45.5, 2020: -11.1, 2021: +66.7✓, 2022: +14.3✓, 2023: -33.3 |
| 5 | kc_mom_p20_m1.3 long, 15m bars | spy | 3731 | +1.9 (+1.6) | +2.0 (+1.6) | +0.008 | 2/5 | 2019: +2.2✓, 2020: -0.4, 2021: +4.4✓, 2022: +7.2, 2023: -2.9 |
| 6 | kc_mr_p6_m1.3 long, 1m bars | all9 | 44263 | +1.4 (+2.9) | +0.8 (+1.4) | +0.010 | 3/5 | 2019: +1.5✓, 2020: +0.7✓, 2021: +3.0✓, 2022: -0.4, 2023: -0.7 |
| 7 | kc_mom_p6_m1.3 short, 15m bars | spy | 1072 | +3.0 (+1.4) | +3.0 (+1.3) | +0.006 | 3/5 | 2019: -1.8, 2020: -0.5, 2021: +7.5✓, 2022: +5.7✓, 2023: +3.8✓ |
| 8 | kc_mom_p20_m2 long, 15m bars | spy | 2616 | +3.1 (+2.2) | +2.0 (+1.3) | +0.011 | 3/5 | 2019: +2.2✓, 2020: -0.4, 2021: +5.7✓, 2022: +6.2✓, 2023: -4.0 |
| 9 | kc_mom_p6_m1.3 long, 15m bars | all9 | 11725 | +2.1 (+2.3) | +1.2 (+1.2) | +0.027 | 3/5 | 2019: -1.2, 2020: -0.6, 2021: +6.6✓, 2022: +1.5✓, 2023: +0.3✓ |
| 10 | box_k0.25_c0 short, 20m bars | spy | 28 | +14.3 (+1.2) | +14.3 (+1.3) | +0.042 | 2/5 | 2019: +0.0, 2020: +12.5✓, 2021: +16.7, 2022: +14.3✓, 2023: +33.3 |

Gap = share our way minus the control taken the same way, in percentage points; ✓ = the year holds.

**Summary.** No rule passes. The breakout box, intraday Keltner (mean reversion and momentum) and the daily
Keltner filter show no direction edge that meets the bar. Four of the 324 tests clear +3 standard errors (about
0.4 expected by chance). They aren't independent: each mirrors a -3 test on the same bars, because Keltner mean
reversion and momentum fire on the same closes in opposite directions.
- **1-minute bars:** after a close below the lower band, price drifts up a little more often than the control
  over the next 10 minutes (kc_mr long, z +3.0 and +3.4; kc_mom short, z -3.7 and -3.4). It fades by 30 minutes,
  and spy doesn't show it.
- **5-minute bars:** after a close above the upper band (P = 6, M = 2), price keeps rising a little more often
  over 30 minutes. kc_mom_p6_m2 long beats the control by 5.3 points (z +3.4) and holds in all 5 years, but at
  10 minutes it is z +2.1, and in spy it is z +0.0 and +1.1.

In rows with at least 300 signals, shares our way are 42-58% and no average move at 30 minutes exceeds +0.08%.
The only options-worthy row is box_k0.15_c0 short on 20-minute bars in all9, with 8 signals (meaningless).

**Breakout box:** no direction edge (shares our way 46-51% in rows with at least 1,000 signals). A box needs
4+ bars in a range of K × daily ATR, which is rare on 15- and 20-minute bars (K = 0.15: under 60 signals in
five years). The races are the one thing worth a follow-up:
- **all9:** the k = 0.25 boxes on 5- and 10-minute bars reach the target before the stop more often than the
  control racing the same distances. Their race expectancy (target first = +target, stop first = -stop,
  neither = 0, % of price) beats the control's by +0.02% to +0.08% per race. It is positive in 10 of 11 all9
  k = 0.25 rows with at least 300 races, with z +3.6 to +4.1 in three. In the two strongest, box_k0.25_c0 long
  and box_k0.25_c1 short on 5-minute bars, it is positive in every year.
- **spy:** it is much weaker (z +0.1 to +1.6).
- **Size:** about 0.05% of the stock price per trade before costs, too small for 0DTE options.

This isn't part of the pass bar and can't count as a pass. A test for T12, set in advance, could settle it.

**Intraday Keltner races:** no edge. The 1-minute mean-reversion races reach the middle line first more often
than the control (+1.7 to +5.6 points), but only because these signals come at volatile moments, when both the
target and the stop get hit more often. Their decided win rate is 49.6-51.2% against a 50% break-even, and the
race expectancy against the control is within ±0.05% everywhere, with no z beyond ±3.

**Daily filter (daily_kc):** no edge. Long after a close below the daily lower band: 585 signals in all9,
52.3% our way at 30 minutes against 49.1% for the control (z +0.8). Short after a close above the upper band:
1,067 signals, 45.5% against 51.3% (z -2.2), so it was the worse side. To 12:00, long 54.9% (z +1.4) and short
44.6% (z -1.7). In spy the counts are below 300.

**FOMC days:** 40 decision days skipped, as in T10b.

## Method

- **Standards (as T10b):** Alpaca 1-minute SIP bars, split-adjusted, regular session; research years 2019-2023 only (2024-2025 holdout untouched); FOMC decision days skipped (40 days, Federal Reserve dates); every rule decides at a bar's close and moves are measured in minutes from that close; entries decided 9:35-11:50; a repeat of the same rule and side within 5 minutes is skipped (Keltner rules).
- **Bar sizes:** 5-, 10-, 15- and 20-minute bars (box) and 1-, 5- and 15-minute bars (intraday Keltner), built from the 1-minute bars and aligned to 9:30.
- **Breakout box:** the most recent stretch of at least 4 bars of today (from 9:30) whose high-low range stays within K × the 14-day daily ATR (Wilder, through yesterday), K = 0.15 and 0.25: for each bar, the longest such stretch ending at the bar before. Signal: a close beyond the box edge plus 0.05% of price (long up, short down); confirmation 0 (that close) or 1 (the next bar also closes beyond the same level; signal at its close). One signal per box: the first close beyond the level uses the box up, and the next box must start after it. Races: 1.0× and 1.618× the box height beyond entry against a stop at the box's opposite edge, within 60 minutes.
- **Intraday Keltner:** middle = simple average of the typical price over P bars; bands = middle ± M × the P-bar ATR (Wilder); P = 6 and 20, M = 1.3 and 2.0. Mean reversion (kc_mr): a close below the lower band → long, above the upper → short; race to the middle line (as it stood at entry) against a stop of the same distance, within 60 minutes. Momentum (kc_mom): a close above the upper band → long, below the lower → short.
- **Daily filter (daily_kc):** daily bars from the regular session; daily Keltner band of 6 days (typical-price average, ± 1.3 × 6-day ATR). A close below the lower band yesterday → long at 9:35 today; above the upper band → short. Measured also at +60 minutes and to 12:00.
- **Control (as T10b):** for each signal, a random entry on the same name at the same time of day within ±5 minutes, on a different random trading day of the same year (never the signal's own day). The pass bar uses the control taken the same way as the signal; the random-direction version is kept. Races: the control races the same distances, as a % of its own entry price, taken the same way.
- **Noise:** every standard error (±) is clustered by day; share gaps use the paired difference between each signal and its own control.
- **Pass bar (unchanged):** at least 300 signals; the share moving our way beats the control taken the same way by at least 3 standard errors at both 10 and 30 minutes; the average move our way is positive at both; it holds in at least 4 of the 5 years; and it holds in both all9 and spy. Options-worthy: at least 57% our way and an average move of at least 0.15% at 30 minutes, in both universes.

## all9: every name, every day

| Rule | Count | Days | Our way 10m | Ctrl 10m | Gap 10m (z) | Our way 30m | Ctrl 30m | Gap 30m (z) | Avg 10m % | Avg 30m % | Years held | Meets bar | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| box_k0.15_c0 long, 5m bars | 4283 | 1030 | 48.7% ±0.9 | 50.5% | -1.8 (-1.5) | 50.3% ±1.0 | 49.9% | +0.4 (+0.4) | +0.002 ±0.004 | +0.007 ±0.009 | 1/5 | no | FAIL |
| box_k0.15_c0 short, 5m bars | 3992 | 1033 | 46.8% ±1.0 | 48.3% | -1.6 (-1.2) | 46.5% ±1.1 | 47.9% | -1.4 (-1.0) | +0.002 ±0.006 | +0.014 ±0.011 | 1/5 | no | FAIL |
| box_k0.15_c0 long, 10m bars | 484 | 293 | 51.0% ±2.6 | 51.9% | -0.8 (-0.2) | 53.1% ±2.6 | 57.9% | -4.8 (-1.4) | +0.015 ±0.011 | +0.028 ±0.022 | 2/5 | no | FAIL |
| box_k0.15_c0 short, 10m bars | 427 | 267 | 42.9% ±2.7 | 45.2% | -2.3 (-0.6) | 42.4% ±2.8 | 48.7% | -6.3 (-1.7) | -0.012 ±0.014 | -0.003 ±0.024 | 0/5 | no | FAIL |
| box_k0.15_c0 long, 15m bars | 57 | 44 | 54.4% ±6.9 | 33.3% | +21.1 (+2.4) | 56.1% ±6.3 | 42.1% | +14.0 (+1.6) | +0.048 ±0.024 | +0.068 ±0.033 | 2/5 | no | FAIL |
| box_k0.15_c0 short, 15m bars | 51 | 39 | 41.2% ±6.9 | 54.9% | -13.7 (-1.6) | 31.4% ±7.6 | 51.0% | -19.6 (-1.9) | -0.017 ±0.028 | -0.043 ±0.048 | 0/5 | no | FAIL |
| box_k0.15_c0 long, 20m bars | 11 | 10 | 45.5% ±17.0 | 63.6% | -18.2 (-0.9) | 63.6% ±16.1 | 72.7% | -9.1 (-0.4) | +0.005 ±0.023 | +0.092 ±0.057 | 0/5 | no | FAIL |
| box_k0.15_c0 short, 20m bars | 8 | 6 | 62.5% ±15.1 | 62.5% | +0.0 (-) | 62.5% ±22.6 | 50.0% | +12.5 (+0.5) | +0.039 ±0.066 | +0.332 ±0.181 | 0/5 | no | FAIL |
| box_k0.15_c1 long, 5m bars | 2804 | 884 | 49.0% ±1.1 | 50.5% | -1.5 (-1.0) | 51.3% ±1.2 | 50.8% | +0.5 (+0.3) | +0.003 ±0.006 | +0.021 ±0.010 | 0/5 | no | FAIL |
| box_k0.15_c1 short, 5m bars | 2527 | 866 | 46.0% ±1.3 | 49.5% | -3.4 (-2.1) | 46.7% ±1.3 | 49.3% | -2.7 (-1.6) | +0.001 ±0.008 | +0.017 ±0.014 | 0/5 | no | FAIL |
| box_k0.15_c1 long, 10m bars | 253 | 176 | 51.0% ±3.5 | 48.6% | +2.4 (+0.5) | 47.0% ±3.5 | 53.8% | -6.7 (-1.6) | -0.007 ±0.017 | -0.008 ±0.032 | 2/5 | no | FAIL |
| box_k0.15_c1 short, 10m bars | 218 | 150 | 42.2% ±3.7 | 49.1% | -6.9 (-1.5) | 44.5% ±4.0 | 50.0% | -5.5 (-1.0) | -0.027 ±0.018 | +0.016 ±0.036 | 0/5 | no | FAIL |
| box_k0.15_c1 long, 15m bars | 22 | 20 | 50.0% ±10.9 | 40.9% | +9.1 (+0.8) | 31.8% ±10.6 | 31.8% | +0.0 (+0.0) | -0.023 ±0.046 | -0.086 ±0.067 | 1/5 | no | FAIL |
| box_k0.15_c1 short, 15m bars | 13 | 13 | 46.2% ±14.4 | 38.5% | +7.7 (+0.3) | 46.2% ±14.4 | 53.8% | -7.7 (-0.4) | -0.004 ±0.088 | +0.010 ±0.051 | 1/5 | no | FAIL |
| box_k0.15_c1 long, 20m bars | 4 | 4 | 50.0% ±28.9 | 75.0% | -25.0 (-1.0) | 50.0% ±28.9 | 50.0% | +0.0 (+0.0) | +0.039 ±0.067 | +0.098 ±0.253 | 0/5 | no | FAIL |
| box_k0.15_c1 short, 20m bars | 2 | 2 | 50.0% ±50.0 | 100.0% | -50.0 (-1.0) | 100.0% ±0.0 | 50.0% | +50.0 (+1.0) | +0.391 ±0.427 | +0.097 ±0.005 | 0/5 | no | FAIL |
| box_k0.25_c0 long, 5m bars | 8782 | 1194 | 48.2% ±0.7 | 50.3% | -2.0 (-2.3) | 50.3% ±0.8 | 51.0% | -0.6 (-0.7) | +0.002 ±0.004 | +0.013 ±0.009 | 0/5 | no | FAIL |
| box_k0.25_c0 short, 5m bars | 8239 | 1178 | 48.4% ±0.8 | 48.7% | -0.3 (-0.3) | 48.2% ±0.9 | 48.2% | -0.0 (-0.0) | +0.006 ±0.006 | +0.014 ±0.011 | 2/5 | no | FAIL |
| box_k0.25_c0 long, 10m bars | 2517 | 836 | 47.4% ±1.3 | 50.7% | -3.4 (-2.1) | 51.2% ±1.2 | 53.2% | -2.0 (-1.2) | +0.001 ±0.006 | +0.018 ±0.010 | 0/5 | no | FAIL |
| box_k0.25_c0 short, 10m bars | 2233 | 788 | 47.8% ±1.4 | 49.6% | -1.8 (-1.0) | 46.7% ±1.5 | 49.5% | -2.9 (-1.6) | +0.013 ±0.008 | +0.026 ±0.014 | 1/5 | no | FAIL |
| box_k0.25_c0 long, 15m bars | 658 | 387 | 46.4% ±2.3 | 53.6% | -7.3 (-2.4) | 51.2% ±2.4 | 51.8% | -0.6 (-0.2) | +0.000 ±0.009 | +0.019 ±0.017 | 0/5 | no | FAIL |
| box_k0.25_c0 short, 15m bars | 559 | 314 | 46.7% ±2.7 | 51.2% | -4.5 (-1.3) | 47.9% ±2.7 | 51.9% | -3.9 (-1.2) | +0.028 ±0.013 | +0.037 ±0.021 | 1/5 | no | FAIL |
| box_k0.25_c0 long, 20m bars | 218 | 149 | 45.9% ±3.9 | 51.4% | -5.5 (-1.1) | 52.3% ±3.8 | 47.2% | +5.0 (+0.9) | -0.001 ±0.013 | +0.015 ±0.020 | 1/5 | no | FAIL |
| box_k0.25_c0 short, 20m bars | 158 | 116 | 48.1% ±4.7 | 45.6% | +2.5 (+0.4) | 50.0% ±4.3 | 47.5% | +2.5 (+0.4) | +0.014 ±0.020 | +0.046 ±0.031 | 1/5 | no | FAIL |
| box_k0.25_c1 long, 5m bars | 5917 | 1112 | 48.4% ±0.8 | 50.9% | -2.6 (-2.4) | 50.6% ±0.9 | 52.3% | -1.7 (-1.5) | +0.001 ±0.005 | +0.016 ±0.010 | 1/5 | no | FAIL |
| box_k0.25_c1 short, 5m bars | 5453 | 1089 | 47.1% ±1.0 | 48.3% | -1.2 (-1.0) | 47.3% ±1.1 | 47.4% | -0.1 (-0.1) | +0.005 ±0.006 | +0.019 ±0.012 | 1/5 | no | FAIL |
| box_k0.25_c1 long, 10m bars | 1510 | 626 | 49.5% ±1.6 | 47.6% | +1.9 (+0.9) | 51.0% ±1.6 | 50.5% | +0.5 (+0.2) | +0.003 ±0.008 | +0.010 ±0.013 | 3/5 | no | FAIL |
| box_k0.25_c1 short, 10m bars | 1359 | 571 | 45.0% ±1.7 | 47.6% | -2.6 (-1.1) | 46.6% ±1.9 | 47.7% | -1.1 (-0.5) | -0.008 ±0.010 | +0.008 ±0.018 | 1/5 | no | FAIL |
| box_k0.25_c1 long, 15m bars | 302 | 212 | 46.0% ±3.0 | 54.6% | -8.6 (-2.1) | 49.7% ±3.2 | 53.6% | -4.0 (-1.0) | -0.009 ±0.013 | +0.010 ±0.025 | 1/5 | no | FAIL |
| box_k0.25_c1 short, 15m bars | 265 | 159 | 49.8% ±4.0 | 47.2% | +2.6 (+0.5) | 52.5% ±4.1 | 46.4% | +6.0 (+1.3) | +0.014 ±0.023 | +0.039 ±0.040 | 2/5 | no | FAIL |
| box_k0.25_c1 long, 20m bars | 61 | 48 | 37.7% ±7.5 | 52.5% | -14.8 (-1.4) | 44.3% ±6.9 | 52.5% | -8.2 (-0.8) | -0.047 ±0.030 | -0.057 ±0.036 | 0/5 | no | FAIL |
| box_k0.25_c1 short, 20m bars | 47 | 41 | 36.2% ±7.7 | 48.9% | -12.8 (-1.3) | 40.4% ±7.9 | 46.8% | -6.4 (-0.7) | -0.019 ±0.047 | -0.078 ±0.080 | 1/5 | no | FAIL |
| kc_mr_p6_m1.3 long, 1m bars | 44263 | 1218 | 51.5% ±0.4 | 50.1% | +1.4 (+2.9) | 51.5% ±0.5 | 50.6% | +0.8 (+1.4) | +0.012 ±0.003 | +0.010 ±0.007 | 3/5 | no | FAIL |
| kc_mr_p6_m1.3 short, 1m bars | 44744 | 1218 | 48.7% ±0.4 | 48.4% | +0.3 (+0.6) | 48.7% ±0.5 | 48.6% | +0.1 (+0.1) | -0.003 ±0.003 | -0.008 ±0.006 | 0/5 | no | FAIL |
| kc_mr_p6_m1.3 long, 5m bars | 13250 | 1154 | 51.2% ±0.7 | 49.7% | +1.4 (+1.8) | 50.4% ±0.9 | 50.4% | +0.0 (+0.0) | +0.011 ±0.007 | +0.004 ±0.015 | 2/5 | no | FAIL |
| kc_mr_p6_m1.3 short, 5m bars | 14607 | 1179 | 49.2% ±0.6 | 48.6% | +0.5 (+0.7) | 47.5% ±0.8 | 49.0% | -1.5 (-1.6) | -0.007 ±0.005 | -0.028 ±0.012 | 0/5 | no | FAIL |
| kc_mr_p6_m1.3 long, 15m bars | 9608 | 908 | 48.1% ±0.8 | 48.8% | -0.7 (-0.7) | 50.1% ±1.1 | 49.4% | +0.7 (+0.6) | -0.011 ±0.008 | +0.011 ±0.016 | 1/5 | no | FAIL |
| kc_mr_p6_m1.3 short, 15m bars | 11725 | 1005 | 47.2% ±0.7 | 48.5% | -1.3 (-1.5) | 47.0% ±0.9 | 48.3% | -1.3 (-1.2) | -0.015 ±0.006 | -0.027 ±0.012 | 0/5 | no | FAIL |
| kc_mr_p6_m2 long, 1m bars | 7252 | 1160 | 52.9% ±0.8 | 50.1% | +2.8 (+2.7) | 52.3% ±0.9 | 51.6% | +0.7 (+0.7) | +0.013 ±0.007 | +0.011 ±0.010 | 3/5 | no | FAIL |
| kc_mr_p6_m2 short, 1m bars | 6483 | 1153 | 48.9% ±0.8 | 48.6% | +0.3 (+0.3) | 49.2% ±0.8 | 48.5% | +0.7 (+0.7) | -0.007 ±0.007 | -0.009 ±0.012 | 2/5 | no | FAIL |
| kc_mr_p6_m2 long, 5m bars | 3732 | 798 | 50.3% ±1.3 | 50.0% | +0.3 (+0.2) | 47.9% ±1.5 | 50.9% | -3.1 (-1.8) | +0.025 ±0.017 | +0.004 ±0.030 | 1/5 | no | FAIL |
| kc_mr_p6_m2 short, 5m bars | 4348 | 876 | 46.9% ±1.1 | 49.0% | -2.1 (-1.6) | 44.4% ±1.3 | 49.0% | -4.6 (-3.0) | -0.029 ±0.010 | -0.077 ±0.020 | 0/5 | no | FAIL |
| kc_mr_p6_m2 long, 15m bars | 3168 | 548 | 45.6% ±1.4 | 49.1% | -3.4 (-2.1) | 47.3% ±1.7 | 50.3% | -3.1 (-1.6) | -0.025 ±0.013 | -0.006 ±0.028 | 1/5 | no | FAIL |
| kc_mr_p6_m2 short, 15m bars | 4150 | 678 | 45.9% ±1.2 | 50.0% | -4.1 (-2.8) | 44.6% ±1.4 | 50.0% | -5.4 (-3.3) | -0.030 ±0.010 | -0.054 ±0.018 | 0/5 | no | FAIL |
| kc_mr_p20_m1.3 long, 1m bars | 77062 | 1218 | 50.9% ±0.4 | 49.6% | +1.3 (+3.0) | 51.0% ±0.6 | 50.4% | +0.6 (+1.0) | +0.005 ±0.003 | +0.006 ±0.007 | 3/5 | no | FAIL |
| kc_mr_p20_m1.3 short, 1m bars | 82073 | 1218 | 48.7% ±0.3 | 48.3% | +0.4 (+1.1) | 48.4% ±0.5 | 48.2% | +0.2 (+0.4) | -0.004 ±0.003 | -0.012 ±0.006 | 0/5 | no | FAIL |
| kc_mr_p20_m1.3 long, 5m bars | 41300 | 1172 | 50.5% ±0.4 | 49.9% | +0.6 (+1.2) | 50.7% ±0.7 | 50.5% | +0.3 (+0.3) | +0.005 ±0.004 | +0.007 ±0.010 | 2/5 | no | FAIL |
| kc_mr_p20_m1.3 short, 5m bars | 48088 | 1177 | 48.8% ±0.4 | 48.7% | +0.1 (+0.3) | 48.1% ±0.6 | 48.5% | -0.4 (-0.7) | -0.005 ±0.003 | -0.014 ±0.008 | 0/5 | no | FAIL |
| kc_mr_p20_m1.3 long, 15m bars | 26001 | 979 | 48.6% ±0.6 | 49.7% | -1.1 (-1.7) | 50.1% ±0.7 | 50.4% | -0.2 (-0.3) | -0.004 ±0.005 | +0.002 ±0.010 | 1/5 | no | FAIL |
| kc_mr_p20_m1.3 short, 15m bars | 32051 | 1066 | 47.2% ±0.5 | 48.6% | -1.5 (-2.5) | 47.4% ±0.7 | 48.2% | -0.8 (-1.1) | -0.008 ±0.003 | -0.017 ±0.007 | 0/5 | no | FAIL |
| kc_mr_p20_m2 long, 1m bars | 44940 | 1218 | 51.8% ±0.4 | 50.0% | +1.7 (+3.4) | 51.0% ±0.6 | 50.6% | +0.5 (+0.7) | +0.009 ±0.004 | +0.004 ±0.009 | 3/5 | no | FAIL |
| kc_mr_p20_m2 short, 1m bars | 47830 | 1218 | 49.4% ±0.4 | 48.5% | +0.9 (+2.0) | 48.4% ±0.6 | 48.5% | -0.1 (-0.1) | -0.002 ±0.003 | -0.012 ±0.007 | 1/5 | no | FAIL |
| kc_mr_p20_m2 long, 5m bars | 27228 | 1097 | 50.3% ±0.5 | 49.4% | +0.9 (+1.5) | 50.9% ±0.8 | 50.3% | +0.6 (+0.7) | +0.006 ±0.005 | +0.012 ±0.012 | 3/5 | no | FAIL |
| kc_mr_p20_m2 short, 5m bars | 32302 | 1146 | 48.4% ±0.5 | 49.3% | -0.9 (-1.6) | 47.5% ±0.7 | 48.7% | -1.2 (-1.5) | -0.008 ±0.004 | -0.021 ±0.009 | 0/5 | no | FAIL |
| kc_mr_p20_m2 long, 15m bars | 17686 | 839 | 48.6% ±0.6 | 49.2% | -0.6 (-0.8) | 50.3% ±0.8 | 50.3% | -0.0 (-0.0) | -0.005 ±0.006 | +0.003 ±0.011 | 1/5 | no | FAIL |
| kc_mr_p20_m2 short, 15m bars | 22420 | 956 | 46.8% ±0.6 | 48.6% | -1.8 (-2.7) | 46.7% ±0.8 | 48.4% | -1.8 (-2.1) | -0.011 ±0.004 | -0.024 ±0.008 | 0/5 | no | FAIL |
| kc_mom_p6_m1.3 long, 1m bars | 44744 | 1218 | 49.6% ±0.4 | 50.2% | -0.6 (-1.2) | 50.4% ±0.5 | 50.6% | -0.2 (-0.3) | +0.003 ±0.003 | +0.008 ±0.006 | 1/5 | no | FAIL |
| kc_mom_p6_m1.3 short, 1m bars | 44263 | 1218 | 47.0% ±0.4 | 48.3% | -1.3 (-2.8) | 47.5% ±0.6 | 48.2% | -0.7 (-1.2) | -0.012 ±0.003 | -0.010 ±0.007 | 0/5 | no | FAIL |
| kc_mom_p6_m1.3 long, 5m bars | 14607 | 1179 | 49.5% ±0.6 | 49.5% | -0.0 (-0.1) | 51.9% ±0.8 | 50.2% | +1.6 (+1.8) | +0.007 ±0.005 | +0.028 ±0.012 | 2/5 | no | FAIL |
| kc_mom_p6_m1.3 short, 5m bars | 13250 | 1154 | 47.7% ±0.7 | 47.3% | +0.4 (+0.5) | 48.9% ±0.9 | 49.0% | -0.2 (-0.2) | -0.011 ±0.007 | -0.004 ±0.015 | 1/5 | no | FAIL |
| kc_mom_p6_m1.3 long, 15m bars | 11725 | 1005 | 51.6% ±0.7 | 49.6% | +2.1 (+2.3) | 52.2% ±0.9 | 51.0% | +1.2 (+1.2) | +0.015 ±0.006 | +0.027 ±0.012 | 3/5 | no | FAIL |
| kc_mom_p6_m1.3 short, 15m bars | 9608 | 908 | 50.9% ±0.8 | 48.8% | +2.1 (+2.1) | 49.2% ±1.1 | 48.1% | +1.1 (+0.9) | +0.011 ±0.008 | -0.011 ±0.016 | 3/5 | no | FAIL |
| kc_mom_p6_m2 long, 1m bars | 6483 | 1153 | 49.4% ±0.8 | 49.9% | -0.5 (-0.5) | 49.7% ±0.9 | 50.2% | -0.5 (-0.5) | +0.007 ±0.007 | +0.009 ±0.012 | 1/5 | no | FAIL |
| kc_mom_p6_m2 short, 1m bars | 7252 | 1160 | 45.6% ±0.8 | 48.9% | -3.4 (-3.4) | 46.7% ±0.9 | 48.8% | -2.1 (-2.0) | -0.013 ±0.007 | -0.011 ±0.010 | 1/5 | no | FAIL |
| kc_mom_p6_m2 long, 5m bars | 4348 | 876 | 52.1% ±1.1 | 49.3% | +2.9 (+2.1) | 55.2% ±1.3 | 49.9% | +5.3 (+3.4) | +0.029 ±0.010 | +0.077 ±0.020 | 5/5 | no | FAIL |
| kc_mom_p6_m2 short, 5m bars | 3732 | 798 | 48.3% ±1.4 | 48.5% | -0.2 (-0.2) | 51.4% ±1.5 | 48.6% | +2.8 (+1.6) | -0.025 ±0.017 | -0.004 ±0.030 | 2/5 | no | FAIL |
| kc_mom_p6_m2 long, 15m bars | 4150 | 678 | 53.3% ±1.2 | 50.5% | +2.9 (+2.1) | 54.7% ±1.4 | 50.9% | +3.8 (+2.3) | +0.030 ±0.010 | +0.054 ±0.018 | 4/5 | no | FAIL |
| kc_mom_p6_m2 short, 15m bars | 3168 | 548 | 53.3% ±1.3 | 50.3% | +3.0 (+1.9) | 52.3% ±1.7 | 50.2% | +2.1 (+1.1) | +0.025 ±0.013 | +0.006 ±0.028 | 3/5 | no | FAIL |
| kc_mom_p20_m1.3 long, 1m bars | 82073 | 1218 | 49.7% ±0.3 | 49.8% | -0.1 (-0.4) | 50.7% ±0.5 | 50.8% | -0.0 (-0.1) | +0.004 ±0.003 | +0.012 ±0.006 | 2/5 | no | FAIL |
| kc_mom_p20_m1.3 short, 1m bars | 77062 | 1218 | 47.6% ±0.4 | 48.5% | -0.8 (-2.1) | 48.1% ±0.6 | 48.1% | -0.0 (-0.0) | -0.005 ±0.003 | -0.006 ±0.007 | 0/5 | no | FAIL |
| kc_mom_p20_m1.3 long, 5m bars | 48088 | 1177 | 49.8% ±0.4 | 49.9% | -0.1 (-0.2) | 51.1% ±0.6 | 50.6% | +0.5 (+0.8) | +0.005 ±0.003 | +0.014 ±0.008 | 1/5 | no | FAIL |
| kc_mom_p20_m1.3 short, 5m bars | 41300 | 1172 | 48.4% ±0.4 | 48.7% | -0.3 (-0.6) | 48.4% ±0.7 | 48.4% | +0.1 (+0.1) | -0.005 ±0.004 | -0.007 ±0.010 | 1/5 | no | FAIL |
| kc_mom_p20_m1.3 long, 15m bars | 32051 | 1066 | 51.3% ±0.5 | 49.1% | +2.3 (+3.9) | 51.6% ±0.7 | 50.8% | +0.8 (+1.1) | +0.008 ±0.003 | +0.017 ±0.007 | 3/5 | no | FAIL |
| kc_mom_p20_m1.3 short, 15m bars | 26001 | 979 | 50.1% ±0.6 | 48.7% | +1.5 (+2.3) | 49.0% ±0.7 | 48.4% | +0.6 (+0.8) | +0.004 ±0.005 | -0.002 ±0.010 | 3/5 | no | FAIL |
| kc_mom_p20_m2 long, 1m bars | 47830 | 1218 | 49.1% ±0.4 | 49.9% | -0.8 (-1.7) | 50.7% ±0.6 | 50.5% | +0.2 (+0.4) | +0.002 ±0.003 | +0.012 ±0.007 | 0/5 | no | FAIL |
| kc_mom_p20_m2 short, 1m bars | 44940 | 1218 | 46.8% ±0.5 | 48.7% | -1.9 (-3.7) | 48.0% ±0.6 | 49.2% | -1.2 (-1.8) | -0.009 ±0.004 | -0.004 ±0.009 | 1/5 | no | FAIL |
| kc_mom_p20_m2 long, 5m bars | 32302 | 1146 | 50.3% ±0.5 | 50.3% | -0.0 (-0.1) | 51.6% ±0.7 | 50.8% | +0.8 (+1.0) | +0.008 ±0.004 | +0.021 ±0.009 | 1/5 | no | FAIL |
| kc_mom_p20_m2 short, 5m bars | 27228 | 1097 | 48.5% ±0.5 | 48.9% | -0.4 (-0.7) | 48.3% ±0.8 | 48.1% | +0.2 (+0.2) | -0.006 ±0.005 | -0.012 ±0.012 | 1/5 | no | FAIL |
| kc_mom_p20_m2 long, 15m bars | 22420 | 956 | 51.8% ±0.6 | 49.9% | +1.9 (+2.7) | 52.3% ±0.8 | 50.8% | +1.6 (+1.9) | +0.011 ±0.004 | +0.024 ±0.008 | 4/5 | no | FAIL |
| kc_mom_p20_m2 short, 15m bars | 17686 | 839 | 50.2% ±0.6 | 48.5% | +1.7 (+2.3) | 48.9% ±0.8 | 48.6% | +0.3 (+0.3) | +0.005 ±0.006 | -0.003 ±0.011 | 1/5 | no | FAIL |
| daily_kc long | 585 | 239 | 46.3% ±3.4 | 51.6% | -5.3 (-1.5) | 52.3% ±3.1 | 49.1% | +3.2 (+0.8) | -0.068 ±0.065 | -0.044 ±0.079 | 0/5 | no | FAIL |
| daily_kc short | 1067 | 434 | 47.0% ±2.2 | 48.4% | -1.4 (-0.5) | 45.5% ±2.1 | 51.3% | -5.8 (-2.2) | -0.047 ±0.023 | -0.055 ±0.035 | 0/5 | no | FAIL |

Daily filter at its extra horizons (control over the same number of minutes):

| Rule | Count | +5m: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|
| daily_kc long | 585 | 48.7% (50.4%, z -0.5), -0.026 ±0.047 | 52.0% (50.4%, z +0.4), +0.074 ±0.093 | 54.9% (49.2%, z +1.4), +0.164 ±0.129 |
| daily_kc short | 1067 | 46.9% (48.7%, z -0.7), -0.027 ±0.019 | 47.0% (49.2%, z -0.8), -0.086 ±0.043 | 44.6% (49.4%, z -1.7), -0.108 ±0.056 |

### Races, all9

**Race to 1.0x box height / to the middle line** (within 60 minutes; target first / stop first / same bar / neither; win rate = target first ÷ (target first + stop first); break-even = the win rate at which target and stop pay the same, from the average distances):

| Rule | Count | Target first | Stop first | Same bar | Neither | Win rate | Control win rate | Gap in target first vs control (z) | Break-even win rate |
|---|---|---|---|---|---|---|---|---|---|
| box_k0.15_c0 long, 5m bars | 4283 | 40.3% | 23.8% | 0.0% | 35.8% | 62.8% | 59.6% | -0.2 (-0.2) | 57.3% |
| box_k0.15_c0 short, 5m bars | 3992 | 43.4% | 25.5% | 0.0% | 31.1% | 63.1% | 61.1% | +2.1 (+1.3) | 57.7% |
| box_k0.15_c0 long, 10m bars | 484 | 31.2% | 13.0% | 0.0% | 55.8% | 70.6% | 65.4% | -6.6 (-2.0) | 58.3% |
| box_k0.15_c0 short, 10m bars | 427 | 33.5% | 15.2% | 0.0% | 51.3% | 68.8% | 65.2% | -4.2 (-1.3) | 58.3% |
| box_k0.15_c0 long, 15m bars | 57 | 29.8% | 1.8% | 0.0% | 68.4% | 94.4% | 50.0% | +3.5 (+0.4) | 56.8% |
| box_k0.15_c0 short, 15m bars | 51 | 35.3% | 13.7% | 0.0% | 51.0% | 72.0% | 70.8% | +2.0 (+0.2) | 58.1% |
| box_k0.15_c0 long, 20m bars | 11 | 9.1% | 0.0% | 0.0% | 90.9% | 100.0% | 80.0% | -27.3 (-1.9) | 55.8% |
| box_k0.15_c1 long, 5m bars | 2804 | 41.2% | 17.7% | 0.0% | 41.2% | 69.9% | 65.3% | -0.6 (-0.4) | 60.8% |
| box_k0.15_c1 short, 5m bars | 2527 | 45.2% | 19.0% | 0.0% | 35.8% | 70.4% | 66.8% | +3.8 (+2.2) | 61.7% |
| box_k0.15_c1 long, 10m bars | 253 | 26.9% | 7.5% | 0.0% | 65.6% | 78.2% | 69.5% | -11.9 (-3.0) | 63.3% |
| box_k0.15_c1 short, 10m bars | 218 | 38.1% | 11.5% | 0.0% | 50.5% | 76.9% | 70.3% | -3.2 (-0.6) | 62.9% |
| box_k0.15_c1 long, 15m bars | 22 | 18.2% | 13.6% | 0.0% | 68.2% | 57.1% | 42.9% | -9.1 (-0.8) | 60.1% |
| box_k0.15_c1 short, 15m bars | 13 | 38.5% | 7.7% | 0.0% | 53.8% | 83.3% | 66.7% | +23.1 (+1.4) | 63.2% |
| box_k0.25_c0 long, 5m bars | 8782 | 29.5% | 17.6% | 0.0% | 52.9% | 62.7% | 58.4% | +0.7 (+0.8) | 55.7% |
| box_k0.25_c0 short, 5m bars | 8239 | 33.0% | 17.7% | 0.0% | 49.3% | 65.1% | 61.3% | +4.0 (+3.6) | 55.9% |
| box_k0.25_c0 long, 10m bars | 2517 | 19.3% | 9.3% | 0.0% | 71.4% | 67.4% | 62.1% | -4.3 (-3.3) | 56.0% |
| box_k0.25_c0 short, 10m bars | 2233 | 25.7% | 8.6% | 0.0% | 65.7% | 74.8% | 61.5% | +1.7 (+1.0) | 56.5% |
| box_k0.25_c0 long, 15m bars | 658 | 15.0% | 3.5% | 0.0% | 81.5% | 81.1% | 60.3% | -3.6 (-1.7) | 56.5% |
| box_k0.25_c0 short, 15m bars | 559 | 22.7% | 3.9% | 0.0% | 73.3% | 85.2% | 67.5% | -0.4 (-0.1) | 56.9% |
| box_k0.25_c0 long, 20m bars | 218 | 6.4% | 0.9% | 0.0% | 92.7% | 87.5% | 63.0% | -9.2 (-3.0) | 56.3% |
| box_k0.25_c0 short, 20m bars | 158 | 22.8% | 0.6% | 0.0% | 76.6% | 97.3% | 62.3% | +1.9 (+0.4) | 57.2% |
| box_k0.25_c1 long, 5m bars | 5917 | 29.0% | 13.5% | 0.0% | 57.5% | 68.2% | 65.5% | -1.0 (-1.0) | 58.7% |
| box_k0.25_c1 short, 5m bars | 5453 | 33.9% | 12.8% | 0.0% | 53.3% | 72.6% | 65.3% | +5.0 (+3.9) | 59.2% |
| box_k0.25_c1 long, 10m bars | 1510 | 18.2% | 5.9% | 0.0% | 75.9% | 75.5% | 62.2% | -2.5 (-1.5) | 59.4% |
| box_k0.25_c1 short, 10m bars | 1359 | 26.6% | 5.7% | 0.0% | 67.7% | 82.5% | 72.9% | +1.3 (+0.6) | 60.2% |
| box_k0.25_c1 long, 15m bars | 302 | 15.2% | 4.0% | 0.0% | 80.8% | 79.3% | 72.2% | -6.3 (-1.9) | 60.2% |
| box_k0.25_c1 short, 15m bars | 265 | 22.3% | 1.9% | 0.0% | 75.8% | 92.2% | 75.4% | +4.9 (+1.2) | 61.3% |
| box_k0.25_c1 long, 20m bars | 61 | 4.9% | 4.9% | 0.0% | 90.2% | 50.0% | 52.6% | -11.5 (-2.1) | 59.6% |
| box_k0.25_c1 short, 20m bars | 47 | 19.1% | 2.1% | 0.0% | 78.7% | 90.0% | 64.3% | +0.0 (+0.0) | 61.7% |
| kc_mr_p20_m1.3 long, 1m bars | 77062 | 47.3% | 47.2% | 0.0% | 5.6% | 50.1% | 49.3% | +4.0 (+8.5) | 50.0% |
| kc_mr_p20_m1.3 short, 1m bars | 82073 | 46.3% | 46.9% | 0.0% | 6.8% | 49.7% | 50.3% | +1.9 (+4.2) | 50.0% |
| kc_mr_p20_m1.3 long, 5m bars | 41300 | 23.8% | 25.2% | 0.0% | 51.0% | 48.5% | 49.2% | +1.3 (+2.2) | 50.0% |
| kc_mr_p20_m1.3 short, 5m bars | 48088 | 22.6% | 21.8% | 0.0% | 55.6% | 50.9% | 50.9% | -1.5 (-2.5) | 50.0% |
| kc_mr_p20_m1.3 long, 15m bars | 26001 | 7.7% | 9.6% | 0.0% | 82.8% | 44.4% | 48.5% | -1.7 (-4.0) | 50.0% |
| kc_mr_p20_m1.3 short, 15m bars | 32051 | 7.9% | 6.5% | 0.0% | 85.6% | 54.5% | 51.7% | -3.1 (-7.8) | 50.0% |
| kc_mr_p20_m2 long, 1m bars | 44940 | 44.9% | 44.7% | 0.0% | 10.5% | 50.1% | 49.4% | +5.6 (+9.3) | 50.0% |
| kc_mr_p20_m2 short, 1m bars | 47830 | 43.4% | 44.1% | 0.0% | 12.4% | 49.6% | 50.2% | +2.9 (+4.9) | 50.0% |
| kc_mr_p20_m2 long, 5m bars | 27228 | 15.9% | 17.5% | 0.0% | 66.6% | 47.7% | 48.4% | -0.0 (-0.0) | 50.0% |
| kc_mr_p20_m2 short, 5m bars | 32302 | 15.4% | 15.2% | 0.0% | 69.4% | 50.4% | 52.0% | -3.3 (-5.8) | 50.0% |
| kc_mr_p20_m2 long, 15m bars | 17686 | 3.2% | 5.0% | 0.0% | 91.8% | 38.8% | 45.3% | -1.6 (-5.3) | 50.0% |
| kc_mr_p20_m2 short, 15m bars | 22420 | 3.7% | 2.8% | 0.0% | 93.5% | 56.6% | 53.1% | -3.1 (-9.6) | 50.0% |
| kc_mr_p6_m1.3 long, 1m bars | 44263 | 50.8% | 48.5% | 0.1% | 0.6% | 51.2% | 49.9% | +3.5 (+7.4) | 50.0% |
| kc_mr_p6_m1.3 short, 1m bars | 44744 | 49.7% | 49.7% | 0.0% | 0.6% | 50.0% | 50.5% | +1.7 (+3.7) | 50.0% |
| kc_mr_p6_m1.3 long, 5m bars | 13250 | 32.0% | 32.8% | 0.0% | 35.1% | 49.4% | 48.5% | +5.1 (+6.2) | 50.0% |
| kc_mr_p6_m1.3 short, 5m bars | 14607 | 29.0% | 31.4% | 0.0% | 39.6% | 48.1% | 51.4% | -1.3 (-1.6) | 50.0% |
| kc_mr_p6_m1.3 long, 15m bars | 9608 | 11.3% | 13.9% | 0.0% | 74.8% | 44.8% | 46.2% | -0.6 (-0.8) | 50.0% |
| kc_mr_p6_m1.3 short, 15m bars | 11725 | 11.3% | 12.1% | 0.0% | 76.6% | 48.4% | 51.1% | -4.1 (-6.0) | 50.0% |
| kc_mr_p6_m2 long, 1m bars | 7252 | 48.6% | 47.2% | 0.0% | 4.1% | 50.7% | 49.8% | +5.7 (+5.8) | 50.0% |
| kc_mr_p6_m2 short, 1m bars | 6483 | 47.4% | 48.2% | 0.0% | 4.4% | 49.6% | 50.9% | +2.6 (+2.6) | 50.0% |
| kc_mr_p6_m2 long, 5m bars | 3732 | 18.9% | 20.4% | 0.0% | 60.7% | 48.2% | 50.0% | +2.1 (+1.8) | 50.0% |
| kc_mr_p6_m2 short, 5m bars | 4348 | 14.9% | 20.1% | 0.0% | 65.1% | 42.6% | 50.5% | -5.5 (-5.3) | 50.0% |
| kc_mr_p6_m2 long, 15m bars | 3168 | 3.8% | 6.6% | 0.0% | 89.7% | 36.4% | 48.2% | -2.1 (-3.3) | 50.0% |
| kc_mr_p6_m2 short, 15m bars | 4150 | 4.4% | 6.1% | 0.0% | 89.5% | 42.2% | 52.1% | -4.2 (-6.4) | 50.0% |
| box_k0.15_c0 short, 20m bars | 8 | 62.5% | 0.0% | 0.0% | 37.5% | 100.0% | 66.7% | +12.5 (+0.5) | 55.8% |
| box_k0.15_c1 long, 20m bars | 4 | 50.0% | 25.0% | 0.0% | 25.0% | 66.7% | 100.0% | +0.0 (+0.0) | 61.6% |
| box_k0.15_c1 short, 20m bars | 2 | 50.0% | 0.0% | 0.0% | 50.0% | 100.0% | 50.0% | +0.0 (+0.0) | 63.1% |

**Race to 1.618x box height** (within 60 minutes; target first / stop first / same bar / neither; win rate = target first ÷ (target first + stop first); break-even = the win rate at which target and stop pay the same, from the average distances):

| Rule | Count | Target first | Stop first | Same bar | Neither | Win rate | Control win rate | Gap in target first vs control (z) | Break-even win rate |
|---|---|---|---|---|---|---|---|---|---|
| box_k0.15_c0 long, 5m bars | 4283 | 19.6% | 25.0% | 0.0% | 55.4% | 43.9% | 42.1% | -2.6 (-2.4) | 45.3% |
| box_k0.15_c0 short, 5m bars | 3992 | 23.4% | 26.8% | 0.0% | 49.8% | 46.7% | 44.6% | +0.0 (+0.0) | 45.8% |
| box_k0.15_c0 long, 10m bars | 484 | 14.7% | 13.0% | 0.0% | 72.3% | 53.0% | 46.5% | -4.3 (-1.7) | 46.3% |
| box_k0.15_c0 short, 10m bars | 427 | 16.4% | 15.5% | 0.0% | 68.1% | 51.5% | 50.0% | -5.4 (-2.0) | 46.4% |
| box_k0.15_c0 long, 15m bars | 57 | 8.8% | 1.8% | 0.0% | 89.5% | 83.3% | 33.3% | -5.3 (-0.9) | 44.8% |
| box_k0.15_c0 short, 15m bars | 51 | 11.8% | 13.7% | 0.0% | 74.5% | 46.2% | 52.6% | -7.8 (-1.1) | 46.1% |
| box_k0.15_c0 long, 20m bars | 11 | 9.1% | 0.0% | 0.0% | 90.9% | 100.0% | 50.0% | +0.0 (+0.0) | 43.9% |
| box_k0.15_c1 long, 5m bars | 2804 | 20.3% | 18.3% | 0.0% | 61.4% | 52.5% | 47.2% | -2.1 (-1.6) | 48.9% |
| box_k0.15_c1 short, 5m bars | 2527 | 23.9% | 19.7% | 0.0% | 56.4% | 54.8% | 49.8% | +0.9 (+0.6) | 49.9% |
| box_k0.15_c1 long, 10m bars | 253 | 13.0% | 7.5% | 0.0% | 79.4% | 63.5% | 54.0% | -8.3 (-2.8) | 51.6% |
| box_k0.15_c1 short, 10m bars | 218 | 21.1% | 11.5% | 0.0% | 67.4% | 64.8% | 55.7% | -3.7 (-0.8) | 51.2% |
| box_k0.15_c1 long, 15m bars | 22 | 4.5% | 13.6% | 0.0% | 81.8% | 25.0% | 27.3% | -9.1 (-1.0) | 48.2% |
| box_k0.15_c1 short, 15m bars | 13 | 0.0% | 7.7% | 0.0% | 92.3% | 0.0% | 50.0% | -7.7 (-1.0) | 51.5% |
| box_k0.25_c0 long, 5m bars | 8782 | 11.1% | 17.9% | 0.0% | 71.0% | 38.1% | 38.0% | -2.2 (-3.4) | 43.7% |
| box_k0.25_c0 short, 5m bars | 8239 | 15.3% | 18.1% | 0.0% | 66.5% | 45.8% | 40.5% | +2.1 (+2.4) | 44.0% |
| box_k0.25_c0 long, 10m bars | 2517 | 5.8% | 9.4% | 0.0% | 84.9% | 38.1% | 38.0% | -3.5 (-4.6) | 44.0% |
| box_k0.25_c0 short, 10m bars | 2233 | 9.6% | 8.8% | 0.0% | 81.6% | 52.3% | 39.9% | -0.7 (-0.6) | 44.6% |
| box_k0.25_c0 long, 15m bars | 658 | 5.2% | 3.5% | 0.0% | 91.3% | 59.6% | 37.8% | -2.6 (-1.9) | 44.6% |
| box_k0.25_c0 short, 15m bars | 559 | 9.8% | 4.1% | 0.0% | 86.0% | 70.5% | 45.4% | +0.2 (+0.1) | 44.9% |
| box_k0.25_c0 long, 20m bars | 218 | 0.9% | 0.9% | 0.0% | 98.2% | 50.0% | 36.4% | -4.6 (-2.8) | 44.3% |
| box_k0.25_c0 short, 20m bars | 158 | 5.1% | 0.6% | 0.0% | 94.3% | 88.9% | 31.0% | -0.6 (-0.2) | 45.3% |
| box_k0.25_c1 long, 5m bars | 5917 | 10.9% | 13.8% | 0.0% | 75.3% | 44.1% | 43.6% | -2.1 (-2.9) | 46.8% |
| box_k0.25_c1 short, 5m bars | 5453 | 15.2% | 13.1% | 0.0% | 71.7% | 53.8% | 44.5% | +2.2 (+2.4) | 47.3% |
| box_k0.25_c1 long, 10m bars | 1510 | 5.2% | 6.0% | 0.0% | 88.8% | 46.7% | 34.9% | -1.8 (-1.9) | 47.5% |
| box_k0.25_c1 short, 10m bars | 1359 | 9.9% | 5.7% | 0.0% | 84.5% | 63.5% | 48.2% | -0.2 (-0.1) | 48.3% |
| box_k0.25_c1 long, 15m bars | 302 | 3.3% | 4.0% | 0.0% | 92.7% | 45.5% | 50.9% | -5.6 (-3.1) | 48.3% |
| box_k0.25_c1 short, 15m bars | 265 | 8.3% | 1.9% | 0.0% | 89.8% | 81.5% | 54.1% | +0.8 (+0.3) | 49.5% |
| box_k0.25_c1 long, 20m bars | 61 | 0.0% | 4.9% | 0.0% | 95.1% | 0.0% | 23.1% | -4.9 (-1.9) | 47.7% |
| box_k0.25_c1 short, 20m bars | 47 | 2.1% | 2.1% | 0.0% | 95.7% | 50.0% | 45.5% | -8.5 (-1.7) | 49.9% |
| box_k0.15_c0 short, 20m bars | 8 | 12.5% | 0.0% | 0.0% | 87.5% | 100.0% | 60.0% | -25.0 (-0.8) | 43.8% |
| box_k0.15_c1 long, 20m bars | 4 | 25.0% | 25.0% | 0.0% | 50.0% | 50.0% | 100.0% | -25.0 (-0.5) | 49.8% |
| box_k0.15_c1 short, 20m bars | 2 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 50.0% | -50.0 (-1.0) | 51.3% |

## spy: SPY only

| Rule | Count | Days | Our way 10m | Ctrl 10m | Gap 10m (z) | Our way 30m | Ctrl 30m | Gap 30m (z) | Avg 10m % | Avg 30m % | Years held | Meets bar | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| box_k0.15_c0 long, 5m bars | 349 | 282 | 49.9% ±2.5 | 54.4% | -4.6 (-1.2) | 57.6% ±2.7 | 51.9% | +5.7 (+1.5) | -0.002 ±0.006 | +0.022 ±0.010 | 2/5 | no | FAIL |
| box_k0.15_c0 short, 5m bars | 334 | 292 | 50.0% ±2.7 | 42.8% | +7.2 (+1.8) | 46.4% ±2.8 | 43.1% | +3.3 (+0.9) | -0.002 ±0.008 | +0.009 ±0.015 | 1/5 | no | FAIL |
| box_k0.15_c0 long, 10m bars | 56 | 53 | 46.4% ±6.6 | 58.9% | -12.5 (-1.4) | 51.8% ±6.4 | 57.1% | -5.4 (-0.6) | +0.013 ±0.011 | -0.010 ±0.025 | 1/5 | no | FAIL |
| box_k0.15_c0 short, 10m bars | 50 | 50 | 40.0% ±7.0 | 50.0% | -10.0 (-0.9) | 46.0% ±7.1 | 50.0% | -4.0 (-0.4) | -0.015 ±0.019 | -0.003 ±0.029 | 1/5 | no | FAIL |
| box_k0.15_c0 long, 15m bars | 11 | 11 | 45.5% ±15.7 | 45.5% | +0.0 (+0.0) | 54.5% ±15.7 | 63.6% | -9.1 (-0.6) | +0.030 ±0.029 | +0.058 ±0.042 | 1/5 | no | FAIL |
| box_k0.15_c0 short, 15m bars | 4 | 4 | 75.0% ±25.0 | 75.0% | +0.0 (+0.0) | 25.0% ±25.0 | 25.0% | +0.0 (-) | +0.079 ±0.043 | +0.010 ±0.042 | 0/5 | no | FAIL |
| box_k0.15_c0 long, 20m bars | 2 | 2 | 100.0% ±0.0 | 50.0% | +50.0 (+1.0) | 100.0% ±0.0 | 0.0% | +100.0 (-) | +0.027 ±0.011 | +0.095 ±0.024 | 1/5 | no | FAIL |
| box_k0.15_c1 long, 5m bars | 229 | 200 | 49.8% ±3.3 | 53.3% | -3.5 (-0.7) | 57.2% ±3.3 | 50.2% | +7.0 (+1.5) | +0.003 ±0.009 | +0.023 ±0.013 | 1/5 | no | FAIL |
| box_k0.15_c1 short, 5m bars | 214 | 199 | 44.4% ±3.5 | 47.7% | -3.3 (-0.7) | 44.4% ±3.4 | 48.6% | -4.2 (-0.9) | +0.009 ±0.010 | +0.008 ±0.017 | 1/5 | no | FAIL |
| box_k0.15_c1 long, 10m bars | 34 | 33 | 50.0% ±8.4 | 76.5% | -26.5 (-2.5) | 47.1% ±8.4 | 73.5% | -26.5 (-2.2) | -0.024 ±0.028 | -0.064 ±0.042 | 0/5 | no | FAIL |
| box_k0.15_c1 short, 10m bars | 30 | 30 | 53.3% ±9.3 | 60.0% | -6.7 (-0.5) | 50.0% ±9.3 | 56.7% | -6.7 (-0.4) | +0.023 ±0.025 | +0.014 ±0.040 | 1/5 | no | FAIL |
| box_k0.15_c1 long, 15m bars | 5 | 5 | 60.0% ±24.5 | 60.0% | +0.0 (+0.0) | 60.0% ±24.5 | 60.0% | +0.0 (+0.0) | +0.023 ±0.052 | +0.019 ±0.108 | 0/5 | no | FAIL |
| box_k0.15_c1 short, 15m bars | 2 | 2 | 0.0% ±0.0 | 50.0% | -50.0 (-1.0) | 0.0% ±0.0 | 100.0% | -100.0 (-) | -0.097 ±0.016 | -0.164 ±0.009 | 0/5 | no | FAIL |
| box_k0.15_c1 long, 20m bars | 1 | 1 | 100.0% ±nan | 100.0% | +0.0 (-) | 100.0% ±nan | 100.0% | +0.0 (-) | +0.030 ±nan | +0.117 ±nan | 0/5 | no | FAIL |
| box_k0.25_c0 long, 5m bars | 714 | 532 | 48.3% ±1.8 | 54.3% | -6.0 (-2.3) | 54.3% ±1.9 | 53.5% | +0.8 (+0.3) | -0.005 ±0.006 | +0.015 ±0.010 | 0/5 | no | FAIL |
| box_k0.25_c0 short, 5m bars | 661 | 511 | 49.8% ±1.9 | 48.3% | +1.5 (+0.5) | 48.9% ±2.0 | 46.9% | +2.0 (+0.7) | -0.003 ±0.007 | +0.005 ±0.012 | 1/5 | no | FAIL |
| box_k0.25_c0 long, 10m bars | 252 | 234 | 51.2% ±3.3 | 51.6% | -0.4 (-0.1) | 56.0% ±3.0 | 54.4% | +1.6 (+0.4) | +0.003 ±0.007 | +0.022 ±0.011 | 2/5 | no | FAIL |
| box_k0.25_c0 short, 10m bars | 198 | 191 | 47.5% ±3.5 | 51.0% | -3.5 (-0.7) | 45.5% ±3.5 | 50.0% | -4.5 (-1.0) | +0.013 ±0.011 | +0.017 ±0.016 | 1/5 | no | FAIL |
| box_k0.25_c0 long, 15m bars | 86 | 86 | 50.0% ±5.4 | 51.2% | -1.2 (-0.2) | 60.5% ±5.3 | 45.3% | +15.1 (+1.9) | +0.001 ±0.011 | +0.034 ±0.020 | 1/5 | no | FAIL |
| box_k0.25_c0 short, 15m bars | 78 | 78 | 37.2% ±5.5 | 51.3% | -14.1 (-1.7) | 42.3% ±5.6 | 53.8% | -11.5 (-1.5) | -0.003 ±0.017 | -0.001 ±0.026 | 0/5 | no | FAIL |
| box_k0.25_c0 long, 20m bars | 35 | 35 | 57.1% ±8.5 | 62.9% | -5.7 (-0.5) | 62.9% ±8.3 | 57.1% | +5.7 (+0.5) | -0.003 ±0.011 | -0.016 ±0.034 | 1/5 | no | FAIL |
| box_k0.25_c0 short, 20m bars | 28 | 28 | 50.0% ±9.6 | 35.7% | +14.3 (+1.2) | 57.1% ±9.5 | 42.9% | +14.3 (+1.3) | +0.035 ±0.021 | +0.042 ±0.026 | 2/5 | no | FAIL |
| box_k0.25_c1 long, 5m bars | 469 | 383 | 50.5% ±2.3 | 53.7% | -3.2 (-1.0) | 53.5% ±2.3 | 54.2% | -0.6 (-0.2) | +0.001 ±0.007 | +0.009 ±0.012 | 2/5 | no | FAIL |
| box_k0.25_c1 short, 5m bars | 422 | 356 | 46.7% ±2.5 | 45.3% | +1.4 (+0.4) | 46.4% ±2.5 | 48.3% | -1.9 (-0.6) | +0.011 ±0.008 | +0.003 ±0.016 | 1/5 | no | FAIL |
| box_k0.25_c1 long, 10m bars | 152 | 145 | 56.6% ±4.1 | 58.6% | -2.0 (-0.3) | 53.3% ±4.0 | 53.9% | -0.7 (-0.1) | +0.018 ±0.014 | -0.000 ±0.019 | 1/5 | no | FAIL |
| box_k0.25_c1 short, 10m bars | 127 | 124 | 40.2% ±4.4 | 41.7% | -1.6 (-0.2) | 40.9% ±4.4 | 43.3% | -2.4 (-0.4) | -0.014 ±0.012 | -0.032 ±0.020 | 0/5 | no | FAIL |
| box_k0.25_c1 long, 15m bars | 43 | 43 | 44.2% ±7.7 | 72.1% | -27.9 (-2.6) | 58.1% ±7.6 | 65.1% | -7.0 (-0.7) | +0.013 ±0.014 | +0.026 ±0.024 | 0/5 | no | FAIL |
| box_k0.25_c1 short, 15m bars | 37 | 37 | 43.2% ±8.3 | 35.1% | +8.1 (+0.8) | 54.1% ±8.3 | 35.1% | +18.9 (+1.7) | -0.012 ±0.029 | +0.002 ±0.043 | 1/5 | no | FAIL |
| box_k0.25_c1 long, 20m bars | 14 | 14 | 57.1% ±13.7 | 64.3% | -7.1 (-0.4) | 50.0% ±13.9 | 50.0% | +0.0 (+0.0) | -0.002 ±0.015 | -0.016 ±0.033 | 1/5 | no | FAIL |
| box_k0.25_c1 short, 20m bars | 10 | 10 | 40.0% ±16.3 | 10.0% | +30.0 (+2.0) | 50.0% ±16.7 | 40.0% | +10.0 (+0.6) | -0.048 ±0.034 | -0.017 ±0.051 | 1/5 | no | FAIL |
| kc_mr_p6_m1.3 long, 1m bars | 4620 | 1203 | 51.8% ±0.7 | 52.1% | -0.4 (-0.4) | 52.2% ±0.9 | 53.4% | -1.2 (-1.1) | +0.003 ±0.003 | -0.001 ±0.005 | 1/5 | no | FAIL |
| kc_mr_p6_m1.3 short, 1m bars | 4651 | 1203 | 48.1% ±0.7 | 49.3% | -1.2 (-1.2) | 46.8% ±0.8 | 49.4% | -2.6 (-2.4) | +0.001 ±0.002 | -0.004 ±0.005 | 0/5 | no | FAIL |
| kc_mr_p6_m1.3 long, 5m bars | 1546 | 755 | 49.9% ±1.2 | 49.4% | +0.5 (+0.3) | 50.4% ±1.4 | 51.6% | -1.2 (-0.6) | -0.003 ±0.005 | -0.007 ±0.010 | 2/5 | no | FAIL |
| kc_mr_p6_m1.3 short, 5m bars | 1578 | 789 | 47.5% ±1.3 | 49.3% | -1.8 (-1.0) | 46.4% ±1.5 | 49.0% | -2.6 (-1.3) | -0.005 ±0.004 | -0.010 ±0.009 | 1/5 | no | FAIL |
| kc_mr_p6_m1.3 long, 15m bars | 1072 | 443 | 48.6% ±1.5 | 49.2% | -0.6 (-0.3) | 49.6% ±1.8 | 50.8% | -1.2 (-0.5) | -0.009 ±0.007 | -0.006 ±0.012 | 0/5 | no | FAIL |
| kc_mr_p6_m1.3 short, 15m bars | 1306 | 498 | 46.3% ±1.4 | 47.9% | -1.5 (-0.8) | 46.0% ±1.6 | 47.5% | -1.5 (-0.7) | -0.008 ±0.005 | -0.012 ±0.009 | 2/5 | no | FAIL |
| kc_mr_p6_m2 long, 1m bars | 809 | 586 | 53.3% ±1.8 | 51.8% | +1.5 (+0.6) | 54.4% ±1.7 | 53.2% | +1.2 (+0.5) | +0.003 ±0.006 | +0.000 ±0.009 | 1/5 | no | FAIL |
| kc_mr_p6_m2 short, 1m bars | 571 | 454 | 48.2% ±2.1 | 49.9% | -1.8 (-0.6) | 46.9% ±2.1 | 46.8% | +0.2 (+0.1) | -0.007 ±0.007 | -0.006 ±0.012 | 2/5 | no | FAIL |
| kc_mr_p6_m2 long, 5m bars | 436 | 316 | 50.2% ±2.5 | 49.5% | +0.7 (+0.2) | 47.0% ±2.7 | 49.8% | -2.8 (-0.7) | +0.008 ±0.011 | -0.005 ±0.022 | 1/5 | no | FAIL |
| kc_mr_p6_m2 short, 5m bars | 455 | 327 | 45.9% ±2.3 | 50.3% | -4.4 (-1.3) | 45.3% ±2.6 | 47.3% | -2.0 (-0.5) | -0.013 ±0.008 | -0.037 ±0.016 | 1/5 | no | FAIL |
| kc_mr_p6_m2 long, 15m bars | 351 | 195 | 43.9% ±2.7 | 49.0% | -5.1 (-1.4) | 43.9% ±3.0 | 49.3% | -5.4 (-1.3) | -0.030 ±0.011 | -0.028 ±0.020 | 0/5 | no | FAIL |
| kc_mr_p6_m2 short, 15m bars | 432 | 216 | 44.7% ±2.6 | 49.1% | -4.4 (-1.3) | 45.4% ±2.7 | 48.6% | -3.2 (-0.9) | -0.014 ±0.008 | -0.015 ±0.014 | 1/5 | no | FAIL |
| kc_mr_p20_m1.3 long, 1m bars | 8388 | 1210 | 51.9% ±0.6 | 51.6% | +0.3 (+0.4) | 52.3% ±0.8 | 52.2% | +0.1 (+0.1) | +0.001 ±0.002 | +0.002 ±0.005 | 1/5 | no | FAIL |
| kc_mr_p20_m1.3 short, 1m bars | 9407 | 1218 | 47.7% ±0.6 | 46.8% | +0.9 (+1.1) | 47.2% ±0.8 | 46.7% | +0.5 (+0.5) | -0.001 ±0.002 | -0.005 ±0.004 | 1/5 | no | FAIL |
| kc_mr_p20_m1.3 long, 5m bars | 4409 | 835 | 51.6% ±0.7 | 51.5% | +0.1 (+0.1) | 52.0% ±1.0 | 51.5% | +0.5 (+0.4) | +0.003 ±0.003 | +0.005 ±0.007 | 2/5 | no | FAIL |
| kc_mr_p20_m1.3 short, 5m bars | 5511 | 917 | 47.8% ±0.7 | 48.5% | -0.7 (-0.7) | 46.8% ±1.0 | 48.4% | -1.6 (-1.3) | -0.002 ±0.002 | -0.004 ±0.005 | 1/5 | no | FAIL |
| kc_mr_p20_m1.3 long, 15m bars | 2743 | 519 | 49.6% ±0.9 | 51.0% | -1.4 (-1.1) | 52.2% ±1.1 | 52.4% | -0.2 (-0.1) | +0.000 ±0.004 | +0.006 ±0.008 | 1/5 | no | FAIL |
| kc_mr_p20_m1.3 short, 15m bars | 3731 | 637 | 46.3% ±0.9 | 46.1% | +0.2 (+0.2) | 45.5% ±1.0 | 45.8% | -0.2 (-0.2) | -0.003 ±0.002 | -0.008 ±0.005 | 1/5 | no | FAIL |
| kc_mr_p20_m2 long, 1m bars | 4938 | 1142 | 51.9% ±0.7 | 51.9% | -0.0 (-0.0) | 51.1% ±0.9 | 51.7% | -0.6 (-0.5) | -0.001 ±0.003 | -0.003 ±0.006 | 1/5 | no | FAIL |
| kc_mr_p20_m2 short, 1m bars | 5334 | 1169 | 48.9% ±0.7 | 46.7% | +2.2 (+2.1) | 46.9% ±0.9 | 46.8% | +0.1 (+0.1) | -0.001 ±0.002 | -0.006 ±0.005 | 1/5 | no | FAIL |
| kc_mr_p20_m2 long, 5m bars | 2961 | 679 | 50.7% ±0.9 | 50.9% | -0.3 (-0.2) | 52.0% ±1.3 | 51.9% | +0.1 (+0.1) | +0.001 ±0.004 | +0.004 ±0.009 | 1/5 | no | FAIL |
| kc_mr_p20_m2 short, 5m bars | 3683 | 737 | 47.2% ±0.8 | 49.0% | -1.8 (-1.6) | 46.8% ±1.2 | 47.5% | -0.7 (-0.5) | -0.004 ±0.002 | -0.008 ±0.006 | 1/5 | no | FAIL |
| kc_mr_p20_m2 long, 15m bars | 1919 | 381 | 49.0% ±1.1 | 49.8% | -0.7 (-0.4) | 51.6% ±1.4 | 49.8% | +1.8 (+1.0) | -0.001 ±0.005 | +0.001 ±0.009 | 0/5 | no | FAIL |
| kc_mr_p20_m2 short, 15m bars | 2616 | 481 | 46.1% ±1.0 | 47.9% | -1.8 (-1.3) | 45.7% ±1.2 | 47.9% | -2.2 (-1.4) | -0.004 ±0.003 | -0.011 ±0.006 | 0/5 | no | FAIL |
| kc_mom_p6_m1.3 long, 1m bars | 4651 | 1203 | 51.1% ±0.7 | 50.8% | +0.3 (+0.3) | 52.8% ±0.8 | 51.8% | +1.0 (+0.9) | -0.001 ±0.002 | +0.004 ±0.005 | 0/5 | no | FAIL |
| kc_mom_p6_m1.3 short, 1m bars | 4620 | 1203 | 47.8% ±0.7 | 47.1% | +0.8 (+0.7) | 47.4% ±0.9 | 46.7% | +0.8 (+0.7) | -0.003 ±0.003 | +0.001 ±0.005 | 0/5 | no | FAIL |
| kc_mom_p6_m1.3 long, 5m bars | 1578 | 789 | 51.4% ±1.3 | 53.0% | -1.6 (-0.9) | 53.2% ±1.5 | 52.9% | +0.3 (+0.2) | +0.005 ±0.004 | +0.010 ±0.009 | 2/5 | no | FAIL |
| kc_mom_p6_m1.3 short, 5m bars | 1546 | 755 | 49.6% ±1.2 | 46.4% | +3.2 (+1.8) | 49.5% ±1.4 | 47.5% | +2.1 (+1.0) | +0.003 ±0.005 | +0.007 ±0.010 | 1/5 | no | FAIL |
| kc_mom_p6_m1.3 long, 15m bars | 1306 | 498 | 52.9% ±1.4 | 51.2% | +1.7 (+0.8) | 53.5% ±1.7 | 52.9% | +0.6 (+0.3) | +0.008 ±0.005 | +0.012 ±0.009 | 3/5 | no | FAIL |
| kc_mom_p6_m1.3 short, 15m bars | 1072 | 443 | 50.8% ±1.5 | 47.9% | +3.0 (+1.4) | 50.2% ±1.8 | 47.2% | +3.0 (+1.3) | +0.009 ±0.007 | +0.006 ±0.012 | 3/5 | no | FAIL |
| kc_mom_p6_m2 long, 1m bars | 571 | 454 | 50.6% ±2.1 | 55.5% | -4.9 (-1.7) | 52.7% ±2.1 | 55.0% | -2.3 (-0.8) | +0.007 ±0.007 | +0.006 ±0.012 | 0/5 | no | FAIL |
| kc_mom_p6_m2 short, 1m bars | 809 | 586 | 46.5% ±1.8 | 47.0% | -0.5 (-0.2) | 45.6% ±1.7 | 43.8% | +1.9 (+0.8) | -0.003 ±0.006 | -0.000 ±0.009 | 2/5 | no | FAIL |
| kc_mom_p6_m2 long, 5m bars | 455 | 327 | 53.6% ±2.3 | 53.6% | +0.0 (+0.0) | 54.1% ±2.6 | 50.1% | +4.0 (+1.1) | +0.013 ±0.008 | +0.037 ±0.016 | 1/5 | no | FAIL |
| kc_mom_p6_m2 short, 5m bars | 436 | 316 | 48.6% ±2.5 | 47.5% | +1.1 (+0.3) | 52.8% ±2.7 | 50.7% | +2.1 (+0.6) | -0.008 ±0.011 | +0.005 ±0.022 | 2/5 | no | FAIL |
| kc_mom_p6_m2 long, 15m bars | 432 | 216 | 53.9% ±2.6 | 51.4% | +2.5 (+0.7) | 53.9% ±2.7 | 52.3% | +1.6 (+0.5) | +0.014 ±0.008 | +0.015 ±0.014 | 2/5 | no | FAIL |
| kc_mom_p6_m2 short, 15m bars | 351 | 195 | 55.6% ±2.7 | 52.1% | +3.4 (+0.9) | 55.8% ±3.0 | 49.6% | +6.3 (+1.6) | +0.030 ±0.011 | +0.028 ±0.020 | 2/5 | no | FAIL |
| kc_mom_p20_m1.3 long, 1m bars | 9407 | 1218 | 51.5% ±0.6 | 51.3% | +0.2 (+0.3) | 52.5% ±0.8 | 52.1% | +0.4 (+0.4) | +0.001 ±0.002 | +0.005 ±0.004 | 1/5 | no | FAIL |
| kc_mom_p20_m1.3 short, 1m bars | 8388 | 1210 | 47.4% ±0.6 | 47.4% | +0.0 (+0.0) | 47.4% ±0.8 | 47.4% | +0.0 (+0.0) | -0.001 ±0.002 | -0.002 ±0.005 | 2/5 | no | FAIL |
| kc_mom_p20_m1.3 long, 5m bars | 5511 | 917 | 51.5% ±0.7 | 50.6% | +0.9 (+0.9) | 52.8% ±1.0 | 52.5% | +0.2 (+0.2) | +0.002 ±0.002 | +0.004 ±0.005 | 2/5 | no | FAIL |
| kc_mom_p20_m1.3 short, 5m bars | 4409 | 835 | 47.8% ±0.8 | 48.2% | -0.4 (-0.4) | 47.8% ±1.0 | 48.2% | -0.4 (-0.3) | -0.003 ±0.003 | -0.005 ±0.007 | 1/5 | no | FAIL |
| kc_mom_p20_m1.3 long, 15m bars | 3731 | 637 | 52.9% ±0.9 | 51.0% | +1.9 (+1.6) | 53.8% ±1.0 | 51.8% | +2.0 (+1.6) | +0.003 ±0.002 | +0.008 ±0.005 | 2/5 | no | FAIL |
| kc_mom_p20_m1.3 short, 15m bars | 2743 | 519 | 49.9% ±0.9 | 47.1% | +2.8 (+2.2) | 47.5% ±1.1 | 47.8% | -0.3 (-0.2) | -0.000 ±0.004 | -0.006 ±0.008 | 1/5 | no | FAIL |
| kc_mom_p20_m2 long, 1m bars | 5334 | 1169 | 50.1% ±0.7 | 51.8% | -1.7 (-1.7) | 52.9% ±0.9 | 52.4% | +0.5 (+0.5) | +0.001 ±0.002 | +0.006 ±0.005 | 0/5 | no | FAIL |
| kc_mom_p20_m2 short, 1m bars | 4938 | 1142 | 47.5% ±0.7 | 47.7% | -0.2 (-0.2) | 48.5% ±1.0 | 47.6% | +0.9 (+0.7) | +0.001 ±0.003 | +0.003 ±0.006 | 2/5 | no | FAIL |
| kc_mom_p20_m2 long, 5m bars | 3683 | 737 | 52.1% ±0.9 | 52.2% | -0.1 (-0.1) | 52.8% ±1.2 | 52.4% | +0.4 (+0.2) | +0.004 ±0.002 | +0.008 ±0.006 | 2/5 | no | FAIL |
| kc_mom_p20_m2 short, 5m bars | 2961 | 679 | 48.7% ±0.9 | 46.8% | +1.8 (+1.4) | 47.7% ±1.3 | 47.0% | +0.7 (+0.4) | -0.001 ±0.004 | -0.004 ±0.009 | 1/5 | no | FAIL |
| kc_mom_p20_m2 long, 15m bars | 2616 | 481 | 53.2% ±1.0 | 50.1% | +3.1 (+2.2) | 53.7% ±1.2 | 51.7% | +2.0 (+1.3) | +0.004 ±0.003 | +0.011 ±0.006 | 3/5 | no | FAIL |
| kc_mom_p20_m2 short, 15m bars | 1919 | 381 | 50.4% ±1.1 | 48.5% | +1.9 (+1.3) | 48.3% ±1.3 | 48.0% | +0.3 (+0.2) | +0.001 ±0.005 | -0.001 ±0.009 | 1/5 | no | FAIL |
| daily_kc long | 77 | 77 | 44.2% ±5.7 | 46.8% | -2.6 (-0.4) | 49.4% ±5.7 | 46.8% | +2.6 (+0.3) | -0.044 ±0.046 | -0.064 ±0.062 | 0/5 | no | FAIL |
| daily_kc short | 109 | 109 | 51.4% ±4.8 | 46.8% | +4.6 (+0.7) | 39.4% ±4.7 | 53.2% | -13.8 (-2.1) | +0.006 ±0.011 | -0.026 ±0.019 | 1/5 | no | FAIL |

Daily filter at its extra horizons (control over the same number of minutes):

| Rule | Count | +5m: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|
| daily_kc long | 77 | 51.9% (40.3%, z +1.5), -0.001 ±0.031 | 48.1% (49.4%, z -0.2), -0.034 ±0.068 | 57.1% (45.5%, z +1.4), +0.061 ±0.107 |
| daily_kc short | 109 | 49.5% (54.1%, z -0.7), +0.001 ±0.010 | 42.2% (45.0%, z -0.4), -0.054 ±0.026 | 37.6% (49.5%, z -2.0), -0.051 ±0.040 |

### Races, spy

**Race to 1.0x box height / to the middle line** (within 60 minutes; target first / stop first / same bar / neither; win rate = target first ÷ (target first + stop first); break-even = the win rate at which target and stop pay the same, from the average distances):

| Rule | Count | Target first | Stop first | Same bar | Neither | Win rate | Control win rate | Gap in target first vs control (z) | Break-even win rate |
|---|---|---|---|---|---|---|---|---|---|
| box_k0.15_c0 long, 5m bars | 349 | 39.8% | 21.2% | 0.0% | 39.0% | 65.3% | 62.7% | -0.6 (-0.2) | 58.4% |
| box_k0.15_c0 short, 5m bars | 334 | 47.3% | 20.4% | 0.0% | 32.3% | 69.9% | 59.8% | +10.8 (+2.8) | 59.4% |
| box_k0.15_c0 long, 10m bars | 56 | 21.4% | 10.7% | 0.0% | 67.9% | 66.7% | 60.6% | -14.3 (-1.7) | 58.4% |
| box_k0.15_c0 short, 10m bars | 50 | 40.0% | 14.0% | 0.0% | 46.0% | 74.1% | 78.6% | -4.0 (-0.4) | 61.1% |
| box_k0.15_c0 short, 15m bars | 4 | 50.0% | 0.0% | 0.0% | 50.0% | 100.0% | 0.0% | +50.0 (+1.7) | 60.0% |
| box_k0.15_c1 long, 5m bars | 229 | 42.8% | 15.7% | 0.0% | 41.5% | 73.1% | 63.0% | +5.7 (+1.3) | 60.9% |
| box_k0.15_c1 short, 5m bars | 214 | 50.9% | 15.4% | 0.0% | 33.6% | 76.8% | 72.0% | +11.2 (+2.5) | 63.8% |
| box_k0.15_c1 long, 10m bars | 34 | 11.8% | 2.9% | 0.0% | 85.3% | 80.0% | 85.7% | -23.5 (-2.7) | 61.2% |
| box_k0.15_c1 short, 10m bars | 30 | 46.7% | 3.3% | 0.0% | 50.0% | 93.3% | 87.5% | +0.0 (+0.0) | 63.6% |
| box_k0.25_c0 long, 5m bars | 714 | 27.6% | 16.5% | 0.0% | 55.9% | 62.5% | 62.5% | +0.0 (+0.0) | 56.4% |
| box_k0.25_c0 short, 5m bars | 661 | 33.7% | 16.3% | 0.0% | 49.9% | 67.4% | 64.3% | +8.2 (+3.1) | 57.4% |
| box_k0.25_c0 long, 10m bars | 252 | 17.1% | 6.3% | 0.0% | 76.6% | 72.9% | 57.6% | -2.4 (-0.7) | 56.6% |
| box_k0.25_c0 short, 10m bars | 198 | 30.8% | 7.1% | 0.0% | 62.1% | 81.3% | 59.7% | +7.6 (+1.6) | 58.0% |
| box_k0.25_c0 long, 15m bars | 86 | 17.4% | 1.2% | 0.0% | 81.4% | 93.8% | 57.1% | +3.5 (+0.6) | 56.0% |
| box_k0.25_c0 short, 15m bars | 78 | 26.9% | 5.1% | 0.0% | 67.9% | 84.0% | 59.1% | +10.3 (+1.5) | 58.4% |
| box_k0.25_c0 long, 20m bars | 35 | 2.9% | 0.0% | 0.0% | 97.1% | 100.0% | 54.5% | -14.3 (-2.4) | 55.9% |
| box_k0.25_c0 short, 20m bars | 28 | 32.1% | 0.0% | 0.0% | 67.9% | 100.0% | 75.0% | +10.7 (+1.1) | 58.6% |
| box_k0.25_c1 long, 5m bars | 469 | 27.5% | 14.3% | 0.0% | 58.2% | 65.8% | 67.3% | -1.5 (-0.6) | 58.9% |
| box_k0.25_c1 short, 5m bars | 422 | 38.6% | 10.9% | 0.0% | 50.5% | 78.0% | 72.4% | +8.8 (+2.8) | 61.1% |
| box_k0.25_c1 long, 10m bars | 152 | 17.1% | 5.3% | 0.0% | 77.6% | 76.5% | 64.3% | -6.6 (-1.4) | 59.2% |
| box_k0.25_c1 short, 10m bars | 127 | 31.5% | 5.5% | 0.0% | 63.0% | 85.1% | 74.5% | +3.9 (+0.7) | 61.9% |
| box_k0.25_c1 long, 15m bars | 43 | 14.0% | 0.0% | 0.0% | 86.0% | 100.0% | 75.0% | -14.0 (-1.8) | 59.8% |
| box_k0.25_c1 short, 15m bars | 37 | 27.0% | 2.7% | 0.0% | 70.3% | 90.9% | 70.0% | +8.1 (+0.9) | 64.2% |
| box_k0.25_c1 long, 20m bars | 14 | 0.0% | 7.1% | 0.0% | 92.9% | 0.0% | 40.0% | -14.3 (-1.5) | 58.5% |
| box_k0.25_c1 short, 20m bars | 10 | 20.0% | 0.0% | 0.0% | 80.0% | 100.0% | 66.7% | +0.0 (+0.0) | 66.6% |
| kc_mr_p20_m1.3 long, 1m bars | 8388 | 48.0% | 46.5% | 0.0% | 5.5% | 50.8% | 49.9% | +6.3 (+7.3) | 50.0% |
| kc_mr_p20_m1.3 short, 1m bars | 9407 | 45.8% | 46.8% | 0.0% | 7.4% | 49.4% | 50.1% | +2.8 (+3.2) | 50.0% |
| kc_mr_p20_m1.3 long, 5m bars | 4409 | 24.6% | 24.1% | 0.0% | 51.3% | 50.4% | 48.4% | +4.7 (+4.5) | 50.0% |
| kc_mr_p20_m1.3 short, 5m bars | 5511 | 21.5% | 18.7% | 0.0% | 59.8% | 53.5% | 52.3% | -2.8 (-2.7) | 50.0% |
| kc_mr_p20_m1.3 long, 15m bars | 2743 | 7.4% | 8.1% | 0.0% | 84.5% | 48.0% | 48.5% | -1.5 (-1.8) | 50.0% |
| kc_mr_p20_m1.3 short, 15m bars | 3731 | 7.3% | 4.3% | 0.0% | 88.4% | 63.0% | 51.2% | -3.9 (-5.0) | 50.0% |
| kc_mr_p20_m2 long, 1m bars | 4938 | 45.1% | 45.4% | 0.0% | 9.5% | 49.8% | 48.5% | +8.6 (+7.9) | 50.0% |
| kc_mr_p20_m2 short, 1m bars | 5334 | 42.1% | 43.5% | 0.1% | 14.3% | 49.2% | 50.2% | +3.3 (+3.0) | 50.0% |
| kc_mr_p20_m2 long, 5m bars | 2961 | 15.9% | 16.0% | 0.0% | 68.1% | 49.9% | 47.2% | +1.6 (+1.4) | 50.0% |
| kc_mr_p20_m2 short, 5m bars | 3683 | 14.6% | 11.0% | 0.0% | 74.4% | 57.1% | 55.5% | -5.3 (-5.0) | 50.0% |
| kc_mr_p20_m2 long, 15m bars | 1919 | 2.8% | 4.6% | 0.0% | 92.7% | 37.6% | 41.9% | -1.6 (-2.5) | 50.0% |
| kc_mr_p20_m2 short, 15m bars | 2616 | 3.7% | 1.5% | 0.0% | 94.8% | 71.9% | 56.6% | -4.7 (-6.7) | 50.0% |
| kc_mr_p6_m1.3 long, 1m bars | 4620 | 51.1% | 48.3% | 0.1% | 0.4% | 51.4% | 50.3% | +5.1 (+5.0) | 50.0% |
| kc_mr_p6_m1.3 short, 1m bars | 4651 | 48.9% | 50.5% | 0.0% | 0.5% | 49.2% | 51.2% | +1.7 (+1.6) | 50.0% |
| kc_mr_p6_m1.3 long, 5m bars | 1546 | 32.2% | 33.7% | 0.0% | 34.1% | 48.9% | 45.4% | +9.2 (+5.7) | 50.0% |
| kc_mr_p6_m1.3 short, 5m bars | 1578 | 24.8% | 28.6% | 0.0% | 46.6% | 46.5% | 52.2% | -4.2 (-2.5) | 50.0% |
| kc_mr_p6_m1.3 long, 15m bars | 1072 | 10.4% | 13.7% | 0.0% | 75.9% | 43.0% | 42.5% | -0.2 (-0.1) | 50.0% |
| kc_mr_p6_m1.3 short, 15m bars | 1306 | 11.1% | 9.7% | 0.0% | 79.2% | 53.3% | 53.3% | -5.8 (-4.0) | 50.0% |
| kc_mr_p6_m2 long, 1m bars | 809 | 47.1% | 48.3% | 0.2% | 4.3% | 49.4% | 48.2% | +9.3 (+3.9) | 50.0% |
| kc_mr_p6_m2 short, 1m bars | 571 | 45.5% | 49.7% | 0.2% | 4.6% | 47.8% | 52.2% | +1.8 (+0.6) | 50.0% |
| kc_mr_p6_m2 long, 5m bars | 436 | 16.5% | 17.0% | 0.0% | 66.5% | 49.3% | 41.3% | +4.6 (+1.9) | 50.0% |
| kc_mr_p6_m2 short, 5m bars | 455 | 11.6% | 12.1% | 0.0% | 76.3% | 49.1% | 50.9% | -7.9 (-3.2) | 50.0% |
| kc_mr_p6_m2 long, 15m bars | 351 | 2.0% | 5.1% | 0.0% | 92.9% | 28.0% | 46.5% | -3.7 (-2.6) | 50.0% |
| kc_mr_p6_m2 short, 15m bars | 432 | 4.6% | 3.0% | 0.0% | 92.4% | 60.6% | 57.1% | -6.5 (-3.5) | 50.0% |
| box_k0.15_c0 long, 15m bars | 11 | 9.1% | 0.0% | 0.0% | 90.9% | 100.0% | 62.5% | -36.4 (-1.8) | 56.2% |
| box_k0.15_c0 long, 20m bars | 2 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 0.0% | +0.0 (-) | 55.0% |
| box_k0.15_c1 long, 15m bars | 5 | 20.0% | 20.0% | 0.0% | 60.0% | 50.0% | 100.0% | +0.0 (-) | 57.1% |
| box_k0.15_c1 short, 15m bars | 2 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 0.0% | +0.0 (-) | 63.2% |
| box_k0.15_c1 long, 20m bars | 1 | 100.0% | 0.0% | 0.0% | 0.0% | 100.0% | 100.0% | +0.0 (-) | 58.2% |

**Race to 1.618x box height** (within 60 minutes; target first / stop first / same bar / neither; win rate = target first ÷ (target first + stop first); break-even = the win rate at which target and stop pay the same, from the average distances):

| Rule | Count | Target first | Stop first | Same bar | Neither | Win rate | Control win rate | Gap in target first vs control (z) | Break-even win rate |
|---|---|---|---|---|---|---|---|---|---|
| box_k0.15_c0 long, 5m bars | 349 | 18.3% | 22.1% | 0.0% | 59.6% | 45.4% | 41.7% | -1.7 (-0.6) | 46.4% |
| box_k0.15_c0 short, 5m bars | 334 | 27.8% | 21.3% | 0.0% | 50.9% | 56.7% | 43.8% | +6.6 (+2.0) | 47.5% |
| box_k0.15_c0 long, 10m bars | 56 | 10.7% | 10.7% | 0.0% | 78.6% | 50.0% | 44.0% | -8.9 (-1.3) | 46.5% |
| box_k0.15_c0 short, 10m bars | 50 | 20.0% | 14.0% | 0.0% | 66.0% | 58.8% | 61.9% | -6.0 (-0.8) | 49.2% |
| box_k0.15_c0 short, 15m bars | 4 | 25.0% | 0.0% | 0.0% | 75.0% | 100.0% | 0.0% | +25.0 (+1.0) | 48.1% |
| box_k0.15_c1 long, 5m bars | 229 | 19.2% | 15.7% | 0.0% | 65.1% | 55.0% | 41.8% | +1.3 (+0.4) | 49.0% |
| box_k0.15_c1 short, 5m bars | 214 | 28.0% | 16.8% | 0.0% | 55.1% | 62.5% | 52.4% | +7.9 (+2.2) | 52.2% |
| box_k0.15_c1 long, 10m bars | 34 | 5.9% | 2.9% | 0.0% | 91.2% | 66.7% | 75.0% | -11.8 (-2.1) | 49.4% |
| box_k0.15_c1 short, 10m bars | 30 | 33.3% | 3.3% | 0.0% | 63.3% | 90.9% | 80.0% | +6.7 (+0.5) | 51.9% |
| box_k0.25_c0 long, 5m bars | 714 | 9.0% | 16.8% | 0.0% | 74.2% | 34.8% | 44.4% | -5.0 (-3.1) | 44.4% |
| box_k0.25_c0 short, 5m bars | 661 | 16.8% | 16.5% | 0.0% | 66.7% | 50.5% | 45.5% | +3.6 (+1.8) | 45.4% |
| box_k0.25_c0 long, 10m bars | 252 | 3.6% | 6.3% | 0.0% | 90.1% | 36.0% | 39.1% | -6.3 (-2.9) | 44.6% |
| box_k0.25_c0 short, 10m bars | 198 | 12.6% | 7.1% | 0.0% | 80.3% | 64.1% | 41.5% | +1.5 (+0.4) | 46.0% |
| box_k0.25_c0 long, 15m bars | 86 | 5.8% | 1.2% | 0.0% | 93.0% | 83.3% | 44.4% | -3.5 (-0.8) | 44.0% |
| box_k0.25_c0 short, 15m bars | 78 | 14.1% | 5.1% | 0.0% | 80.8% | 73.3% | 40.0% | +3.8 (+0.7) | 46.5% |
| box_k0.25_c0 long, 20m bars | 35 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 28.6% | -5.7 (-1.4) | 43.9% |
| box_k0.25_c0 short, 20m bars | 28 | 14.3% | 0.0% | 0.0% | 85.7% | 100.0% | 50.0% | +7.1 (+0.8) | 46.7% |
| box_k0.25_c1 long, 5m bars | 469 | 9.2% | 14.5% | 0.0% | 76.3% | 38.7% | 42.7% | -2.8 (-1.5) | 47.0% |
| box_k0.25_c1 short, 5m bars | 422 | 18.2% | 11.1% | 0.0% | 70.6% | 62.1% | 55.4% | +3.6 (+1.4) | 49.2% |
| box_k0.25_c1 long, 10m bars | 152 | 3.9% | 5.3% | 0.0% | 90.8% | 42.9% | 44.7% | -7.2 (-2.5) | 47.3% |
| box_k0.25_c1 short, 10m bars | 127 | 11.0% | 5.5% | 0.0% | 83.5% | 66.7% | 57.6% | -3.9 (-1.0) | 50.1% |
| box_k0.25_c1 long, 15m bars | 43 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 60.0% | -14.0 (-2.6) | 47.9% |
| box_k0.25_c1 short, 15m bars | 37 | 8.1% | 2.7% | 0.0% | 89.2% | 75.0% | 57.1% | -2.7 (-0.4) | 52.5% |
| box_k0.25_c1 long, 20m bars | 14 | 0.0% | 7.1% | 0.0% | 92.9% | 0.0% | 25.0% | -7.1 (-1.0) | 46.5% |
| box_k0.25_c1 short, 20m bars | 10 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 50.0% | -10.0 (-1.0) | 55.2% |
| box_k0.15_c0 long, 15m bars | 11 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 50.0% | -27.3 (-1.9) | 44.3% |
| box_k0.15_c0 long, 20m bars | 2 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 0.0% | +0.0 (-) | 43.0% |
| box_k0.15_c1 long, 15m bars | 5 | 0.0% | 20.0% | 0.0% | 80.0% | 0.0% | 100.0% | -20.0 (-1.0) | 45.2% |
| box_k0.15_c1 short, 15m bars | 2 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 0.0% | +0.0 (-) | 51.5% |
| box_k0.15_c1 long, 20m bars | 1 | 0.0% | 0.0% | 0.0% | 100.0% | 0.0% | 100.0% | -100.0 (-) | 46.3% |

The year-by-year tables for every row are in the full report.

---

Full per-trade tables: [history/2026-10-28-t11-box-keltner.md](history/2026-10-28-t11-box-keltner.md)
