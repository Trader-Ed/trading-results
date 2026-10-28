# T10: five-year research bench, first test suite (2019-2023)

**Comparisons: 98 rule × side × bar-size candidates, each judged in all9 and spy (196 rows, 392 tests of the 3-standard-error bar at 10 and 30 minutes); atr_pick is shown for comparison only.** If no rule had any edge, a single test clears 3 standard errors one time in about 740, so about 0.5 of the 392 tests would clear it by chance, and a full PASS (both horizons, 4 of 5 years, both universes) would almost never happen by chance (well under 0.1 expected).

## Findings

**PASS (by the bar as written):** b3_touch long, 1m bars; b3_reentry long, 1m bars. See below before reading anything into it.

**By the bar as written, two rows pass (b3_touch long and b3_reentry long, 1-minute bars), but neither
is an edge.** They clear the bar only because the control is biased (diagnostic below). On their own they move
our way 50.6% and 50.9% of the time at 10 minutes (51.2% and 51.5% at 30), with an average move of about
+0.005% at 30 minutes: far below the options-worthy mark (57%, +0.15%) and below any trading cost. Neither is
options-worthy.

**The control as specified is biased.** A control time drawn in the signal's half hour but earlier than the
signal measures a window that contains the move that created the signal. So the control "taken the same way"
moves with the move into the signal, not at random. After 1-minute b3 and r2 signals (price just fell, for a long)
it loses 0.06-0.09% in 10 minutes. After trend and breakout signals (e1, squeeze, pullback, opening range, first
half hour; price just rose, for a long) it gains 0.02-0.23%. That is why the 1-minute mean-reversion rules show
large positive gaps (+8 to +13 points, z up to +50) and the trend and breakout rules large negative ones (down to
-19 points). This is the control moving, not the signal. All 10 strongest results below are b3 rows for this
reason. The bias shrinks or flips with bar size as the move into the signal changes. For example, r2 on 3- to
5-minute bars, which needs a bar closing beyond the previous bar's high, gets a rising control and negative gaps.

**With a control that can't share the signal's move, nothing passes.** Against the random-direction control, no
rule × side × bar size clears 3 standard errors at both 10 and 30 minutes in both all9 and spy. The few rows that
clear it in one universe (b3_touch long: +1.4 to +1.9 points in all9 at 1- and 2-minute bars, +3.7 to +4.3 in spy
at 4-minute bars) are matched by b3_touch short falling short of random by about as much. That pattern is market
drift over 2019-2023, not direction. In rows with at least 300 signals, the rules' own shares our way are 44-59%,
and average moves are within ±0.09% at 10 and 30 minutes. Across the rulebook's squeeze and pullback rules, Ed's
six rules, opening-range breakouts, gap continuation and fill, and the first half hour, there is no direction edge
in 2019-2023.

**For the next suite (a partner decision; not changed here):** keep the same name and half hour, but draw the
control from a different day, or only from times after the signal, so it can't share the signal's own move. The
bench reruns all of T10 in under 4 minutes.

**The 10 strongest results** (all9 and spy rows, ranked by the smaller of the 10- and 30-minute z):

| # | Rule | Universe | Count | Gap 10m (z) | Gap 30m (z) | Avg 30m % | Years held | Year by year: gap 30m (pts) |
|---|---|---|---|---|---|---|---|---|
| 1 | b3_touch long, 1m bars | all9 | 88733 | +10.9 (+47.4) | +9.6 (+49.7) | +0.005 | 4/5 | 2019: +9.3✓, 2020: +9.8✓, 2021: +10.3✓, 2022: +9.0, 2023: +9.5✓ |
| 2 | b3_touch short, 1m bars | all9 | 91505 | +9.8 (+43.7) | +8.7 (+44.6) | -0.006 | 1/5 | 2019: +8.3, 2020: +8.0, 2021: +9.1, 2022: +9.2✓, 2023: +9.1 |
| 3 | b3_touch long, 2m bars | all9 | 60969 | +12.3 (+42.1) | +10.7 (+41.8) | +0.003 | 3/5 | 2019: +10.7, 2020: +11.3✓, 2021: +11.1✓, 2022: +9.8, 2023: +10.7✓ |
| 4 | b3_touch short, 2m bars | all9 | 63045 | +11.1 (+39.6) | +9.7 (+39.8) | -0.008 | 1/5 | 2019: +8.8, 2020: +9.1, 2021: +9.7, 2022: +11.2✓, 2023: +9.8 |
| 5 | b3_touch long, 3m bars | all9 | 48963 | +11.4 (+34.4) | +9.5 (+34.2) | +0.003 | 3/5 | 2019: +9.0, 2020: +10.3✓, 2021: +10.4✓, 2022: +7.4, 2023: +10.3✓ |
| 6 | b3_reentry long, 1m bars | all9 | 34184 | +12.6 (+33.0) | +11.1 (+35.5) | +0.006 | 4/5 | 2019: +10.0✓, 2020: +11.2✓, 2021: +12.4✓, 2022: +10.3, 2023: +11.8✓ |
| 7 | b3_touch short, 3m bars | all9 | 51552 | +9.9 (+31.5) | +8.4 (+33.3) | -0.012 | 1/5 | 2019: +7.4, 2020: +8.7, 2021: +8.5, 2022: +9.3✓, 2023: +8.3 |
| 8 | b3_reentry short, 1m bars | all9 | 33386 | +11.3 (+30.1) | +9.6 (+30.6) | -0.007 | 2/5 | 2019: +8.0, 2020: +9.4, 2021: +10.5, 2022: +9.6✓, 2023: +10.2✓ |
| 9 | b3_touch short, 4m bars | all9 | 36878 | +9.0 (+25.6) | +7.6 (+26.1) | -0.013 | 0/5 | 2019: +6.8, 2020: +7.4, 2021: +8.1, 2022: +8.3, 2023: +7.7 |
| 10 | b3_touch long, 4m bars | all9 | 34932 | +10.1 (+26.9) | +8.4 (+25.6) | +0.007 | 2/5 | 2019: +8.8, 2020: +8.8✓, 2021: +9.1, 2022: +6.4, 2023: +8.5✓ |

Gap = share our way minus the control taken the same way, in percentage points; ✓ = the year holds.

## Diagnostic: the same-half-hour control overlaps the move behind each signal

The control's own average move depends on which rule fired. A control time drawn earlier in the signal's half hour measures a window that contains the move that made the signal (the fall into a band touch, the rise into a trend signal), so the control taken the same way is pushed against mean-reversion rules and towards trend rules. The table shows it for all9 at 1-minute bars: the control's average move taken the same way is far from zero, and its sign follows the kind of rule.

| Rule (all9, 1m bars) | Count | Our way 10m | Avg 10m % | Ctrl taken same way: our way 10m | its avg 10m % | Random-direction ctrl: our way 10m | Gap vs same-way ctrl (z) | Gap vs random-direction ctrl (z) |
|---|---|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 2120 | 50.0% | +0.009 | 62.1% | +0.073 | 48.9% | -12.1 (-8.7) | +1.2 (+0.7) |
| squeeze short, 1m bars | 1945 | 48.8% | +0.018 | 61.4% | +0.080 | 48.6% | -12.5 (-7.9) | +0.2 (+0.1) |
| pullback long, 1m bars | 2965 | 49.9% | +0.007 | 58.5% | +0.054 | 49.6% | -8.6 (-7.5) | +0.3 (+0.2) |
| pullback short, 1m bars | 2445 | 47.3% | -0.005 | 56.9% | +0.045 | 48.9% | -9.6 (-7.6) | -1.6 (-1.1) |
| e1_trend long, 1m bars | 58924 | 50.1% | +0.003 | 56.4% | +0.047 | 49.2% | -6.3 (-21.9) | +0.9 (+2.1) |
| e1_trend short, 1m bars | 56786 | 48.5% | -0.003 | 55.7% | +0.044 | 48.8% | -7.2 (-24.1) | -0.3 (-0.8) |
| e1_reject long, 1m bars | 93981 | 49.6% | +0.002 | 59.8% | +0.063 | 49.3% | -10.2 (-48.8) | +0.3 (+0.9) |
| e1_reject short, 1m bars | 87553 | 48.1% | -0.002 | 58.8% | +0.063 | 49.0% | -10.8 (-46.7) | -1.0 (-2.5) |
| r2_rsi long, 1m bars | 14344 | 50.4% | -0.002 | 40.5% | -0.080 | 49.7% | +9.9 (+16.4) | +0.6 (+0.8) |
| r2_rsi short, 1m bars | 9523 | 47.6% | -0.012 | 39.1% | -0.081 | 49.4% | +8.5 (+12.8) | -1.8 (-2.2) |
| r2_rsi_sym long, 1m bars | 8250 | 51.6% | +0.001 | 39.6% | -0.086 | 49.9% | +12.0 (+15.9) | +1.6 (+1.7) |
| r2_rsi_sym short, 1m bars | 9523 | 47.6% | -0.012 | 39.0% | -0.079 | 50.5% | +8.6 (+12.7) | -2.9 (-3.5) |
| b3_touch long, 1m bars | 88733 | 50.6% | +0.006 | 39.8% | -0.060 | 49.2% | +10.9 (+47.4) | +1.4 (+3.9) |
| b3_touch short, 1m bars | 91505 | 48.5% | -0.003 | 38.7% | -0.061 | 49.3% | +9.8 (+43.7) | -0.9 (-2.4) |
| b3_reentry long, 1m bars | 34184 | 50.9% | +0.006 | 38.3% | -0.076 | 49.4% | +12.6 (+33.0) | +1.5 (+3.0) |
| b3_reentry short, 1m bars | 33386 | 48.7% | -0.005 | 37.4% | -0.081 | 49.7% | +11.3 (+30.1) | -1.0 (-2.0) |
| orb15 long, 1m bars | 2177 | 50.8% | +0.024 | 64.1% | +0.145 | 49.9% | -13.3 (-9.4) | +0.9 (+0.6) |
| orb15 short, 1m bars | 1982 | 46.3% | -0.016 | 65.4% | +0.152 | 49.5% | -19.1 (-12.7) | -3.2 (-1.9) |
| orb30 long, 1m bars | 2287 | 50.8% | +0.016 | 62.8% | +0.095 | 49.4% | -12.0 (-8.9) | +1.4 (+0.9) |
| orb30 short, 1m bars | 2232 | 47.3% | +0.002 | 61.4% | +0.105 | 48.5% | -14.1 (-9.1) | -1.2 (-0.7) |
| gap0.5_cont long | 3326 | 49.1% | -0.005 | 51.2% | +0.017 | 49.4% | -2.1 (-1.3) | -0.3 (-0.2) |
| gap0.5_cont short | 2806 | 51.0% | +0.010 | 50.0% | -0.007 | 49.1% | +1.1 (+0.6) | +1.9 (+1.0) |
| gap0.5_fill long | 2806 | 47.5% | -0.010 | 48.3% | -0.003 | 49.9% | -0.8 (-0.4) | -2.3 (-1.2) |
| gap0.5_fill short | 3326 | 50.0% | +0.005 | 46.7% | -0.017 | 50.2% | +3.3 (+2.2) | -0.2 (-0.1) |
| gap1_cont long | 1717 | 49.6% | -0.003 | 53.3% | +0.037 | 48.6% | -3.7 (-1.8) | +1.0 (+0.5) |
| gap1_cont short | 1584 | 50.3% | +0.009 | 51.8% | -0.010 | 49.6% | -1.5 (-0.6) | +0.8 (+0.3) |
| gap1_fill long | 1584 | 47.8% | -0.009 | 48.4% | +0.002 | 48.0% | -0.6 (-0.3) | -0.2 (-0.1) |
| gap1_fill short | 1717 | 49.7% | +0.003 | 46.4% | -0.024 | 48.7% | +3.3 (+1.5) | +0.9 (+0.4) |
| first_half_hour long | 3808 | 50.0% | +0.008 | 65.9% | +0.189 | 49.9% | -15.8 (-11.5) | +0.1 (+0.1) |
| first_half_hour short | 3355 | 52.2% | +0.029 | 66.7% | +0.189 | 50.4% | -14.6 (-9.6) | +1.7 (+1.0) |

With the random-direction control instead (all other parts of the bar except the year test unchanged), rows meeting the 3-standard-error bar at both 10 and 30 minutes with a positive average move in both all9 and spy: none.

## Check: the October 27 signal test, reproduced with the bench's code

Same period (2026-01-02 to 2026-10-23), same cached bars and day frames, 1-minute bars, default rulebook. The bench's vectorized rules are compared with the live rules (machine/rules.py evaluate()) on every bar in the entry window; then the signals are combined as the live rules do (squeeze first, pullbacks only from 10:00), moves are measured with the bench's price lookup, the October 27 random control is redrawn (seed 7), and every row is compared with the October 27 CSV.

| Run | Bars compared | Rule answers that differ | Rows Oct 27 / now | Squeeze | Pullback | Control | Same rows (day, name, time, setup, side) | Largest move difference |
|---|---|---|---|---|---|---|---|---|
| ATR pick | 26928 | 0 | 266 / 266 | 69 / 69 | 64 / 64 | 133 / 133 | yes | 0.0e+00 points |
| SPY | 26928 | 0 | 246 / 246 | 50 / 50 | 73 / 73 | 123 / 123 | yes | 0.0e+00 points |

**Result: reproduced exactly.**

## The bench

- **Bars:** 1-minute SIP bars from Alpaca, split-adjusted, regular session only (half days end at 13:00), for
  AAPL, AMZN, NVDA, MSFT, META, GOOGL, TSLA, SPY and QQQ, 2019-01-02 to 2025-12-31, plus December 2018 to warm up
  the indicators and give the prior close for 2019-01-02. 1,258 sessions in 2019-2023 for every name, each day
  starting at 9:30; split days show no jump (the largest overnight gaps are earnings days and March 2020).
- **Storage:** one compressed file per symbol and year (72 files), 72 MB in all.
- **Download time:** 5 minutes 42 seconds, in two parallel downloads.
- **Holdout lock:** 2024-01-01 to 2025-12-31. The bench refuses those dates unless run with `--holdout` and a
  written partner-approval note, and logs every such run to state/holdout_log. Nothing in T10 touched the
  holdout; the holdout log is empty.

## Method

- **Data:** Alpaca 1-minute SIP bars, split-adjusted, regular session only, AAPL, AMZN, NVDA, MSFT, META, GOOGL, TSLA, SPY and QQQ. Research years 2019-2023 only; 2024-2025 is the holdout and was not used. Indicators run on the continuous regular-session series (the previous sessions warm them up).
- **Bar sizes:** 2-, 3-, 4- and 5-minute bars are built from the 1-minute bars, aligned to 9:30. Every rule decides at a bar's close; moves are measured from that close in minutes, on the 1-minute prices (the price at time T is the close of the last 1-minute bar ending by T).
- **Rules:** the current rulebook's squeeze rule (breakout) and pullback rules (with the chop filter and the VWAP warm-up to 10:00), and Ed's rules with the T9 definitions, each tested on its own (no squeeze priority, no 10:00 squeeze-only limit), with the bar size as a setting; entries decided 9:35-11:50. A repeat of the same rule and side within 5 minutes of the last recorded one is skipped (as in T9). Opening-range breakout: range 9:30-9:45 or 9:30-10:00, the first later bar (1- or 5-minute) decided by 11:30 that closes beyond the range with volume at least 1.5× the range's average bar volume, one per day. Gap: 9:30 open vs the prior close; continuation and fill at the 9:35 close. First half hour: 9:30 open to 10:00 moves at least 0.3%; signal at 10:00.
- **Control:** for each signal, a random 1-minute decision time on the same name and day, in the same half hour (9:31-10:00, 10:01-10:30, ..., within 9:35-11:50). Long signals are compared with the control taken long and short signals with the control taken short (this removes the market's drift), and those comparisons decide the pass bar.
- **Noise:** every standard error (±) is clustered by day: signals on the same day, on any name, count as one cluster. The share gap's standard error uses the paired difference between each signal and its own control. z = gap / its standard error.
- **Universes:** all9 (every name, every day), spy (SPY only), atr_pick (the rulebook's weekday universe and ATR % pick, from daily bars built from the regular session; Fed days are not skipped as the rulebook lists only 2026 dates).
- **Pass bar (fixed in advance):** at least 300 signals; the share moving our way beats the control taken the same way by at least 3 standard errors at both 10 and 30 minutes; the average move our way is positive at both; it holds in at least 4 of the 5 years (a year holds when the share beats the control and the average move is positive at both 10 and 30 minutes); and it holds in both all9 and spy. Options-worthy: at least 57% our way at 30 minutes and an average move of at least 0.15% at 30 minutes, in both universes.

## all9: every name, every day

| Rule | Count | Days | Our way 10m | Ctrl 10m | Gap 10m (z) | Our way 30m | Ctrl 30m | Gap 30m (z) | Avg 10m % | Avg 30m % | Years held | Meets bar | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 2120 | 930 | 50.0% ±1.1 | 62.1% | -12.1 (-8.7) | 49.8% ±1.3 | 61.6% | -11.8 (-10.7) | +0.009 ±0.007 | +0.000 ±0.012 | 0/5 | no | FAIL |
| squeeze short, 1m bars | 1945 | 900 | 48.8% ±1.3 | 61.4% | -12.5 (-7.9) | 49.4% ±1.3 | 59.9% | -10.5 (-9.0) | +0.018 ±0.009 | +0.026 ±0.014 | 0/5 | no | FAIL |
| squeeze long, 2m bars | 798 | 514 | 53.0% ±1.9 | 65.0% | -12.0 (-5.4) | 52.0% ±2.0 | 65.8% | -13.8 (-8.1) | +0.027 ±0.012 | +0.042 ±0.022 | 0/5 | no | FAIL |
| squeeze short, 2m bars | 690 | 462 | 47.8% ±2.1 | 64.9% | -17.1 (-6.7) | 47.7% ±2.2 | 65.4% | -17.7 (-8.5) | +0.028 ±0.012 | +0.038 ±0.023 | 0/5 | no | FAIL |
| squeeze long, 3m bars | 569 | 386 | 52.0% ±2.3 | 56.4% | -4.4 (-1.6) | 52.2% ±2.3 | 60.8% | -8.6 (-4.2) | +0.045 ±0.020 | +0.093 ±0.035 | 0/5 | no | FAIL |
| squeeze short, 3m bars | 499 | 333 | 49.9% ±2.6 | 57.1% | -7.2 (-2.3) | 48.1% ±2.6 | 58.5% | -10.4 (-4.3) | -0.017 ±0.027 | -0.017 ±0.035 | 0/5 | no | FAIL |
| squeeze long, 4m bars | 548 | 360 | 54.7% ±2.3 | 56.2% | -1.5 (-0.5) | 52.4% ±2.5 | 54.6% | -2.2 (-1.0) | +0.064 ±0.024 | +0.088 ±0.043 | 2/5 | no | FAIL |
| squeeze short, 4m bars | 414 | 268 | 49.8% ±3.2 | 51.7% | -1.9 (-0.6) | 51.0% ±2.9 | 58.5% | -7.5 (-2.7) | -0.001 ±0.038 | -0.007 ±0.049 | 1/5 | no | FAIL |
| squeeze long, 5m bars | 714 | 384 | 49.0% ±2.3 | 49.4% | -0.4 (-0.1) | 51.4% ±2.2 | 51.8% | -0.4 (-0.2) | +0.005 ±0.026 | +0.030 ±0.039 | 2/5 | no | FAIL |
| squeeze short, 5m bars | 610 | 364 | 49.2% ±2.4 | 51.1% | -2.0 (-0.7) | 48.2% ±2.4 | 50.7% | -2.5 (-1.0) | -0.019 ±0.027 | +0.009 ±0.046 | 0/5 | no | FAIL |
| pullback long, 1m bars | 2965 | 983 | 49.9% ±1.0 | 58.5% | -8.6 (-7.5) | 50.4% ±1.1 | 59.7% | -9.3 (-10.8) | +0.007 ±0.006 | +0.022 ±0.012 | 0/5 | no | FAIL |
| pullback short, 1m bars | 2445 | 942 | 47.3% ±1.1 | 56.9% | -9.6 (-7.6) | 46.3% ±1.3 | 55.8% | -9.5 (-9.4) | -0.005 ±0.007 | -0.014 ±0.012 | 0/5 | no | FAIL |
| pullback long, 2m bars | 954 | 605 | 50.8% ±1.6 | 60.1% | -9.2 (-4.4) | 49.6% ±1.7 | 63.4% | -13.8 (-8.7) | +0.004 ±0.013 | +0.003 ±0.021 | 0/5 | no | FAIL |
| pullback short, 2m bars | 779 | 521 | 46.2% ±1.9 | 59.4% | -13.2 (-5.8) | 47.0% ±2.0 | 59.1% | -12.1 (-7.0) | -0.005 ±0.013 | -0.007 ±0.020 | 0/5 | no | FAIL |
| pullback long, 3m bars | 552 | 413 | 50.0% ±2.2 | 59.1% | -9.1 (-3.5) | 50.0% ±2.3 | 63.8% | -13.8 (-6.8) | +0.028 ±0.021 | +0.046 ±0.037 | 0/5 | no | FAIL |
| pullback short, 3m bars | 464 | 359 | 49.6% ±2.4 | 60.1% | -10.6 (-3.6) | 45.5% ±2.5 | 58.2% | -12.7 (-5.6) | -0.020 ±0.019 | -0.031 ±0.033 | 0/5 | no | FAIL |
| pullback long, 4m bars | 391 | 310 | 48.3% ±2.7 | 53.7% | -5.4 (-1.8) | 47.1% ±2.8 | 55.2% | -8.2 (-3.2) | -0.029 ±0.029 | -0.035 ±0.042 | 0/5 | no | FAIL |
| pullback short, 4m bars | 366 | 296 | 51.6% ±2.7 | 61.2% | -9.6 (-2.9) | 50.0% ±2.8 | 58.2% | -8.2 (-3.2) | +0.008 ±0.026 | +0.042 ±0.046 | 0/5 | no | FAIL |
| pullback long, 5m bars | 489 | 344 | 48.3% ±2.5 | 54.0% | -5.7 (-2.0) | 48.1% ±2.5 | 51.3% | -3.3 (-1.3) | -0.021 ±0.026 | -0.050 ±0.041 | 0/5 | no | FAIL |
| pullback short, 5m bars | 488 | 365 | 50.4% ±2.4 | 60.0% | -9.6 (-3.5) | 51.0% ±2.5 | 59.8% | -8.8 (-3.5) | +0.024 ±0.022 | +0.012 ±0.043 | 0/5 | no | FAIL |
| e1_trend long, 1m bars | 58924 | 1258 | 50.1% ±0.3 | 56.4% | -6.3 (-21.9) | 50.2% ±0.5 | 56.7% | -6.5 (-28.4) | +0.003 ±0.002 | +0.005 ±0.006 | 0/5 | no | FAIL |
| e1_trend short, 1m bars | 56786 | 1258 | 48.5% ±0.4 | 55.7% | -7.2 (-24.1) | 48.3% ±0.5 | 55.3% | -7.1 (-30.6) | -0.003 ±0.003 | -0.007 ±0.006 | 0/5 | no | FAIL |
| e1_trend long, 2m bars | 29701 | 1257 | 49.5% ±0.4 | 57.0% | -7.5 (-18.8) | 50.3% ±0.6 | 58.2% | -7.9 (-24.2) | -0.001 ±0.003 | +0.006 ±0.007 | 0/5 | no | FAIL |
| e1_trend short, 2m bars | 28499 | 1256 | 48.5% ±0.5 | 56.6% | -8.1 (-18.8) | 48.0% ±0.6 | 57.2% | -9.3 (-26.5) | -0.003 ±0.003 | -0.004 ±0.007 | 0/5 | no | FAIL |
| e1_trend long, 3m bars | 19339 | 1243 | 49.8% ±0.5 | 58.8% | -9.0 (-18.8) | 49.9% ±0.6 | 59.4% | -9.4 (-24.1) | +0.000 ±0.004 | +0.005 ±0.008 | 0/5 | no | FAIL |
| e1_trend short, 3m bars | 18363 | 1250 | 48.5% ±0.5 | 57.8% | -9.3 (-17.9) | 48.6% ±0.7 | 57.4% | -8.8 (-21.6) | -0.004 ±0.004 | -0.003 ±0.008 | 0/5 | no | FAIL |
| e1_trend long, 4m bars | 14148 | 1227 | 49.5% ±0.5 | 59.5% | -9.9 (-18.2) | 49.4% ±0.7 | 59.2% | -9.8 (-22.8) | -0.002 ±0.004 | -0.003 ±0.008 | 0/5 | no | FAIL |
| e1_trend short, 4m bars | 13501 | 1237 | 48.1% ±0.6 | 59.3% | -11.2 (-19.4) | 48.6% ±0.7 | 59.0% | -10.4 (-21.9) | -0.003 ±0.004 | -0.005 ±0.009 | 0/5 | no | FAIL |
| e1_trend long, 5m bars | 12958 | 1216 | 49.0% ±0.6 | 58.9% | -9.9 (-16.6) | 49.3% ±0.7 | 58.8% | -9.5 (-19.0) | -0.007 ±0.005 | -0.001 ±0.009 | 0/5 | no | FAIL |
| e1_trend short, 5m bars | 12190 | 1212 | 47.7% ±0.6 | 58.4% | -10.6 (-16.4) | 48.7% ±0.7 | 58.1% | -9.4 (-18.3) | -0.012 ±0.005 | -0.008 ±0.010 | 0/5 | no | FAIL |
| e1_reject long, 1m bars | 93981 | 1258 | 49.6% ±0.3 | 59.8% | -10.2 (-48.8) | 50.4% ±0.5 | 58.9% | -8.4 (-46.5) | +0.002 ±0.002 | +0.007 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 1m bars | 87553 | 1258 | 48.1% ±0.3 | 58.8% | -10.8 (-46.7) | 48.2% ±0.5 | 57.3% | -9.2 (-45.9) | -0.002 ±0.002 | -0.004 ±0.006 | 0/5 | no | FAIL |
| e1_reject long, 2m bars | 65609 | 1256 | 49.3% ±0.4 | 59.1% | -9.8 (-37.6) | 50.2% ±0.5 | 58.4% | -8.2 (-39.0) | +0.001 ±0.002 | +0.005 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 2m bars | 58746 | 1257 | 48.0% ±0.4 | 58.3% | -10.3 (-35.4) | 47.8% ±0.6 | 56.7% | -8.8 (-37.3) | -0.001 ±0.003 | -0.002 ±0.007 | 0/5 | no | FAIL |
| e1_reject long, 3m bars | 49763 | 1242 | 49.7% ±0.4 | 58.1% | -8.5 (-27.0) | 50.2% ±0.6 | 58.0% | -7.8 (-31.6) | +0.001 ±0.003 | +0.005 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 3m bars | 44012 | 1246 | 48.0% ±0.4 | 57.2% | -9.2 (-27.3) | 47.8% ±0.6 | 56.0% | -8.2 (-30.4) | -0.005 ±0.003 | -0.007 ±0.007 | 0/5 | no | FAIL |
| e1_reject long, 4m bars | 36347 | 1222 | 49.9% ±0.4 | 58.1% | -8.2 (-22.7) | 50.4% ±0.6 | 57.5% | -7.1 (-25.5) | +0.001 ±0.003 | +0.005 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 4m bars | 31705 | 1224 | 48.2% ±0.5 | 56.5% | -8.4 (-21.4) | 47.9% ±0.7 | 55.6% | -7.8 (-24.2) | -0.004 ±0.003 | -0.005 ±0.007 | 0/5 | no | FAIL |
| e1_reject long, 5m bars | 28715 | 1205 | 49.3% ±0.4 | 57.5% | -8.2 (-22.0) | 50.1% ±0.6 | 57.9% | -7.8 (-24.5) | -0.000 ±0.003 | +0.006 ±0.006 | 0/5 | no | FAIL |
| e1_reject short, 5m bars | 25028 | 1198 | 48.2% ±0.5 | 56.7% | -8.5 (-19.2) | 47.8% ±0.7 | 56.4% | -8.6 (-24.4) | -0.006 ±0.004 | -0.002 ±0.008 | 0/5 | no | FAIL |
| r2_rsi long, 1m bars | 14344 | 1220 | 50.4% ±0.6 | 40.5% | +9.9 (+16.4) | 50.6% ±0.8 | 42.4% | +8.3 (+16.8) | -0.002 ±0.005 | -0.001 ±0.011 | 3/5 | no | FAIL |
| r2_rsi short, 1m bars | 9523 | 1182 | 47.6% ±0.7 | 39.1% | +8.5 (+12.8) | 47.8% ±0.8 | 40.6% | +7.2 (+13.4) | -0.012 ±0.005 | -0.015 ±0.010 | 1/5 | no | FAIL |
| r2_rsi long, 2m bars | 8933 | 1075 | 49.3% ±0.8 | 46.3% | +3.0 (+3.8) | 49.8% ±1.0 | 47.3% | +2.5 (+4.1) | -0.006 ±0.007 | +0.001 ±0.013 | 2/5 | no | FAIL |
| r2_rsi short, 2m bars | 5867 | 1049 | 47.1% ±0.8 | 47.1% | +0.0 (+0.0) | 46.7% ±1.0 | 47.0% | -0.3 (-0.4) | -0.022 ±0.006 | -0.033 ±0.012 | 0/5 | no | FAIL |
| r2_rsi long, 3m bars | 7727 | 999 | 49.0% ±0.8 | 51.2% | -2.3 (-2.8) | 49.1% ±1.0 | 52.7% | -3.6 (-5.7) | -0.006 ±0.007 | -0.006 ±0.014 | 0/5 | no | FAIL |
| r2_rsi short, 3m bars | 4517 | 971 | 46.4% ±0.9 | 49.7% | -3.4 (-3.6) | 45.7% ±1.0 | 49.3% | -3.6 (-5.0) | -0.021 ±0.007 | -0.041 ±0.013 | 0/5 | no | FAIL |
| r2_rsi long, 4m bars | 6389 | 944 | 49.6% ±0.9 | 55.1% | -5.5 (-6.5) | 50.4% ±1.1 | 55.0% | -4.7 (-6.6) | -0.005 ±0.008 | +0.006 ±0.015 | 0/5 | no | FAIL |
| r2_rsi short, 4m bars | 3774 | 920 | 45.0% ±1.0 | 53.9% | -8.9 (-8.2) | 47.0% ±1.1 | 53.6% | -6.5 (-8.1) | -0.017 ±0.008 | -0.027 ±0.014 | 0/5 | no | FAIL |
| r2_rsi long, 5m bars | 5700 | 929 | 48.5% ±1.0 | 56.2% | -7.8 (-8.1) | 49.0% ±1.1 | 57.2% | -8.2 (-10.6) | -0.017 ±0.008 | -0.012 ±0.015 | 0/5 | no | FAIL |
| r2_rsi short, 5m bars | 3345 | 893 | 46.7% ±1.1 | 54.1% | -7.4 (-6.3) | 46.0% ±1.2 | 55.4% | -9.4 (-9.7) | -0.016 ±0.008 | -0.019 ±0.015 | 0/5 | no | FAIL |
| r2_rsi_sym long, 1m bars | 8250 | 1160 | 51.6% ±0.8 | 39.6% | +12.0 (+15.9) | 51.2% ±0.9 | 41.7% | +9.5 (+15.1) | +0.001 ±0.006 | +0.006 ±0.012 | 3/5 | no | FAIL |
| r2_rsi_sym short, 1m bars | 9523 | 1182 | 47.6% ±0.7 | 39.0% | +8.6 (+12.7) | 47.8% ±0.8 | 40.4% | +7.4 (+13.3) | -0.012 ±0.005 | -0.015 ±0.010 | 1/5 | no | FAIL |
| r2_rsi_sym long, 2m bars | 4846 | 960 | 49.7% ±1.0 | 46.2% | +3.5 (+3.5) | 50.6% ±1.1 | 49.0% | +1.5 (+2.0) | +0.001 ±0.009 | +0.009 ±0.015 | 2/5 | no | FAIL |
| r2_rsi_sym short, 2m bars | 5867 | 1049 | 47.1% ±0.8 | 44.8% | +2.3 (+2.7) | 46.7% ±1.0 | 46.0% | +0.7 (+1.1) | -0.022 ±0.006 | -0.033 ±0.012 | 0/5 | no | FAIL |
| r2_rsi_sym long, 3m bars | 3860 | 869 | 49.2% ±1.0 | 50.8% | -1.6 (-1.4) | 49.9% ±1.2 | 51.6% | -1.6 (-1.8) | -0.010 ±0.009 | +0.007 ±0.016 | 0/5 | no | FAIL |
| r2_rsi_sym short, 3m bars | 4517 | 971 | 46.4% ±0.9 | 49.9% | -3.5 (-3.6) | 45.7% ±1.0 | 49.8% | -4.1 (-5.3) | -0.021 ±0.007 | -0.041 ±0.013 | 0/5 | no | FAIL |
| r2_rsi_sym long, 4m bars | 3141 | 806 | 51.4% ±1.1 | 54.8% | -3.4 (-2.7) | 51.4% ±1.3 | 56.5% | -5.0 (-5.3) | +0.008 ±0.010 | +0.024 ±0.017 | 0/5 | no | FAIL |
| r2_rsi_sym short, 4m bars | 3774 | 920 | 45.0% ±1.0 | 52.6% | -7.6 (-7.0) | 47.0% ±1.1 | 54.6% | -7.5 (-9.2) | -0.017 ±0.008 | -0.027 ±0.014 | 0/5 | no | FAIL |
| r2_rsi_sym long, 5m bars | 2853 | 788 | 50.1% ±1.2 | 55.2% | -5.2 (-3.9) | 49.8% ±1.3 | 56.7% | -6.9 (-6.6) | -0.013 ±0.011 | -0.007 ±0.017 | 0/5 | no | FAIL |
| r2_rsi_sym short, 5m bars | 3345 | 893 | 46.7% ±1.1 | 57.5% | -10.9 (-9.7) | 46.0% ±1.2 | 55.8% | -9.9 (-10.8) | -0.016 ±0.008 | -0.019 ±0.015 | 0/5 | no | FAIL |
| b3_touch long, 1m bars | 88733 | 1258 | 50.6% ±0.3 | 39.8% | +10.9 (+47.4) | 51.2% ±0.5 | 41.6% | +9.6 (+49.7) | +0.006 ±0.002 | +0.005 ±0.006 | 4/5 | yes | PASS |
| b3_touch short, 1m bars | 91505 | 1258 | 48.5% ±0.3 | 38.7% | +9.8 (+43.7) | 48.5% ±0.5 | 39.8% | +8.7 (+44.6) | -0.003 ±0.002 | -0.006 ±0.005 | 1/5 | no | FAIL |
| b3_touch long, 2m bars | 60969 | 1258 | 51.0% ±0.4 | 38.7% | +12.3 (+42.1) | 51.5% ±0.6 | 40.8% | +10.7 (+41.8) | +0.004 ±0.003 | +0.003 ±0.006 | 3/5 | no | FAIL |
| b3_touch short, 2m bars | 63045 | 1258 | 48.7% ±0.4 | 37.7% | +11.1 (+39.6) | 48.6% ±0.5 | 38.9% | +9.7 (+39.8) | -0.005 ±0.002 | -0.008 ±0.006 | 1/5 | no | FAIL |
| b3_touch long, 3m bars | 48963 | 1255 | 50.5% ±0.4 | 39.1% | +11.4 (+34.4) | 51.4% ±0.6 | 41.9% | +9.5 (+34.2) | +0.002 ±0.003 | +0.003 ±0.008 | 3/5 | no | FAIL |
| b3_touch short, 3m bars | 51552 | 1255 | 48.6% ±0.4 | 38.7% | +9.9 (+31.5) | 48.3% ±0.6 | 40.0% | +8.4 (+33.3) | -0.005 ±0.003 | -0.012 ±0.007 | 1/5 | no | FAIL |
| b3_touch long, 4m bars | 34932 | 1244 | 50.5% ±0.5 | 40.4% | +10.1 (+26.9) | 51.3% ±0.7 | 43.0% | +8.4 (+25.6) | +0.001 ±0.004 | +0.007 ±0.009 | 2/5 | no | FAIL |
| b3_touch short, 4m bars | 36878 | 1239 | 48.4% ±0.5 | 39.4% | +9.0 (+25.6) | 48.3% ±0.6 | 40.7% | +7.6 (+26.1) | -0.006 ±0.003 | -0.013 ±0.008 | 0/5 | no | FAIL |
| b3_touch long, 5m bars | 29173 | 1235 | 50.5% ±0.5 | 41.5% | +9.0 (+23.4) | 51.2% ±0.7 | 43.7% | +7.6 (+23.3) | +0.005 ±0.004 | +0.008 ±0.010 | 3/5 | no | FAIL |
| b3_touch short, 5m bars | 31599 | 1229 | 48.6% ±0.5 | 40.8% | +7.9 (+21.1) | 48.3% ±0.7 | 41.5% | +6.8 (+22.7) | -0.008 ±0.004 | -0.017 ±0.009 | 0/5 | no | FAIL |
| b3_reentry long, 1m bars | 34184 | 1258 | 50.9% ±0.4 | 38.3% | +12.6 (+33.0) | 51.5% ±0.6 | 40.3% | +11.1 (+35.5) | +0.006 ±0.003 | +0.006 ±0.007 | 4/5 | yes | PASS |
| b3_reentry short, 1m bars | 33386 | 1258 | 48.7% ±0.4 | 37.4% | +11.3 (+30.1) | 48.4% ±0.5 | 38.9% | +9.6 (+30.6) | -0.005 ±0.003 | -0.007 ±0.006 | 2/5 | no | FAIL |
| b3_reentry long, 2m bars | 19655 | 1254 | 50.5% ±0.6 | 39.2% | +11.4 (+21.4) | 51.1% ±0.7 | 41.1% | +9.9 (+23.5) | -0.000 ±0.005 | -0.000 ±0.009 | 3/5 | no | FAIL |
| b3_reentry short, 2m bars | 19695 | 1254 | 49.3% ±0.5 | 39.3% | +10.0 (+19.7) | 48.4% ±0.7 | 39.8% | +8.6 (+20.8) | -0.007 ±0.004 | -0.016 ±0.009 | 0/5 | no | FAIL |
| b3_reentry long, 3m bars | 14315 | 1227 | 49.7% ±0.6 | 42.5% | +7.2 (+11.9) | 50.8% ±0.8 | 44.7% | +6.1 (+13.2) | +0.001 ±0.006 | +0.005 ±0.011 | 2/5 | no | FAIL |
| b3_reentry short, 3m bars | 14651 | 1231 | 48.6% ±0.6 | 41.2% | +7.4 (+12.5) | 48.2% ±0.7 | 42.2% | +5.9 (+12.9) | -0.004 ±0.005 | -0.015 ±0.010 | 0/5 | no | FAIL |
| b3_reentry long, 4m bars | 10997 | 1197 | 50.0% ±0.7 | 44.1% | +5.9 (+8.7) | 51.1% ±0.9 | 46.5% | +4.6 (+8.9) | -0.002 ±0.006 | +0.009 ±0.013 | 2/5 | no | FAIL |
| b3_reentry short, 4m bars | 11436 | 1202 | 48.9% ±0.7 | 43.2% | +5.7 (+9.0) | 48.5% ±0.8 | 45.0% | +3.5 (+7.2) | -0.005 ±0.005 | -0.009 ±0.011 | 1/5 | no | FAIL |
| b3_reentry long, 5m bars | 9886 | 1167 | 49.4% ±0.8 | 46.0% | +3.4 (+4.5) | 51.1% ±0.9 | 47.8% | +3.3 (+6.1) | -0.011 ±0.007 | +0.012 ±0.013 | 1/5 | no | FAIL |
| b3_reentry short, 5m bars | 10395 | 1185 | 48.1% ±0.7 | 45.4% | +2.6 (+3.9) | 49.0% ±0.8 | 46.4% | +2.5 (+5.1) | -0.005 ±0.006 | -0.011 ±0.011 | 2/5 | no | FAIL |
| orb15 long, 1m bars | 2177 | 868 | 50.8% ±1.2 | 64.1% | -13.3 (-9.4) | 52.1% ±1.3 | 62.9% | -10.7 (-9.2) | +0.024 ±0.010 | +0.034 ±0.016 | 0/5 | no | FAIL |
| orb15 short, 1m bars | 1982 | 777 | 46.3% ±1.3 | 65.4% | -19.1 (-12.7) | 48.6% ±1.5 | 63.8% | -15.2 (-12.3) | -0.016 ±0.014 | -0.004 ±0.020 | 0/5 | no | FAIL |
| orb15 long, 5m bars | 334 | 236 | 49.4% ±3.1 | 66.5% | -17.1 (-5.2) | 51.8% ±3.1 | 66.5% | -14.7 (-4.5) | -0.014 ±0.025 | +0.027 ±0.036 | 0/5 | no | FAIL |
| orb15 short, 5m bars | 372 | 238 | 49.7% ±2.8 | 63.7% | -14.0 (-4.4) | 49.2% ±3.0 | 62.1% | -12.9 (-4.8) | +0.003 ±0.038 | +0.011 ±0.043 | 0/5 | no | FAIL |
| orb30 long, 1m bars | 2287 | 847 | 50.8% ±1.2 | 62.8% | -12.0 (-8.9) | 52.5% ±1.3 | 61.8% | -9.3 (-7.9) | +0.016 ±0.008 | +0.018 ±0.015 | 0/5 | no | FAIL |
| orb30 short, 1m bars | 2232 | 760 | 47.3% ±1.3 | 61.4% | -14.1 (-9.1) | 47.6% ±1.5 | 61.7% | -14.1 (-12.0) | +0.002 ±0.011 | +0.016 ±0.017 | 0/5 | no | FAIL |
| orb30 long, 5m bars | 418 | 299 | 50.2% ±2.8 | 60.5% | -10.3 (-3.2) | 53.6% ±2.8 | 64.4% | -10.8 (-4.1) | -0.029 ±0.028 | -0.030 ±0.035 | 0/5 | no | FAIL |
| orb30 short, 5m bars | 468 | 278 | 49.4% ±2.6 | 65.4% | -16.0 (-5.1) | 48.3% ±2.9 | 66.7% | -18.4 (-7.4) | -0.011 ±0.020 | +0.011 ±0.032 | 0/5 | no | FAIL |
| gap0.5_cont long | 3326 | 841 | 49.1% ±1.5 | 51.2% | -2.1 (-1.3) | 53.7% ±1.5 | 52.1% | +1.6 (+1.2) | -0.005 ±0.019 | +0.050 ±0.029 | 1/5 | no | FAIL |
| gap0.5_cont short | 2806 | 708 | 51.0% ±1.7 | 50.0% | +1.1 (+0.6) | 55.0% ±1.7 | 50.1% | +4.9 (+3.5) | +0.010 ±0.022 | +0.042 ±0.036 | 1/5 | no | FAIL |
| gap0.5_fill long | 2806 | 708 | 47.5% ±1.7 | 48.3% | -0.8 (-0.4) | 44.1% ±1.7 | 49.7% | -5.6 (-3.9) | -0.010 ±0.022 | -0.042 ±0.036 | 0/5 | no | FAIL |
| gap0.5_fill short | 3326 | 841 | 50.0% ±1.5 | 46.7% | +3.3 (+2.2) | 45.9% ±1.5 | 46.2% | -0.3 (-0.2) | +0.005 ±0.019 | -0.050 ±0.029 | 1/5 | no | FAIL |
| gap1_cont long | 1717 | 599 | 49.6% ±1.9 | 53.3% | -3.7 (-1.8) | 55.7% ±1.9 | 55.4% | +0.3 (+0.2) | -0.003 ±0.030 | +0.091 ±0.044 | 1/5 | no | FAIL |
| gap1_cont short | 1584 | 505 | 50.3% ±2.2 | 51.8% | -1.5 (-0.6) | 54.5% ±2.2 | 49.2% | +5.4 (+3.0) | +0.009 ±0.032 | +0.030 ±0.051 | 0/5 | no | FAIL |
| gap1_fill long | 1584 | 505 | 47.8% ±2.2 | 48.4% | -0.6 (-0.3) | 44.7% ±2.2 | 47.9% | -3.2 (-1.7) | -0.009 ±0.032 | -0.030 ±0.051 | 1/5 | no | FAIL |
| gap1_fill short | 1717 | 599 | 49.7% ±1.9 | 46.4% | +3.3 (+1.5) | 43.8% ±1.9 | 45.0% | -1.2 (-0.6) | +0.003 ±0.030 | -0.091 ±0.044 | 0/5 | no | FAIL |
| first_half_hour long | 3808 | 1045 | 50.0% ±1.4 | 65.9% | -15.8 (-11.5) | 52.3% ±1.3 | 66.9% | -14.6 (-13.1) | +0.008 ±0.013 | +0.031 ±0.019 | 0/5 | no | FAIL |
| first_half_hour short | 3355 | 984 | 52.2% ±1.5 | 66.7% | -14.6 (-9.6) | 50.2% ±1.5 | 64.7% | -14.5 (-12.2) | +0.029 ±0.015 | -0.002 ±0.025 | 0/5 | no | FAIL |

Gap and first-half-hour rules at their extra horizons (control over the same number of minutes):

| Rule | Count | +5m: our way (ctrl), avg % | to 10:00: our way (ctrl), avg % | to 10:30: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|---|---|
| gap0.5_cont long | 3326 | 49.4% (51.4%, z -1.2), -0.013 ±0.015 | 53.1% (52.2%, z +0.7), +0.030 ±0.027 | 52.3% (52.6%, z -0.3), +0.041 ±0.034 | 52.3% (52.2%, z +0.1), +0.055 ±0.036 | 52.9% (52.6%, z +0.3), +0.079 ±0.049 |
| gap0.5_cont short | 2806 | 47.5% (50.3%, z -1.5), -0.016 ±0.017 | 51.7% (51.1%, z +0.4), -0.017 ±0.034 | 50.5% (50.1%, z +0.3), -0.038 ±0.046 | 50.6% (49.7%, z +0.8), -0.023 ±0.049 | 50.9% (50.5%, z +0.4), -0.037 ±0.062 |
| gap0.5_fill long | 2806 | 51.0% (48.0%, z +1.8), +0.016 ±0.017 | 48.0% (48.6%, z -0.4), +0.017 ±0.034 | 49.3% (49.9%, z -0.5), +0.038 ±0.046 | 49.1% (49.7%, z -0.5), +0.023 ±0.049 | 48.8% (49.8%, z -0.9), +0.037 ±0.062 |
| gap0.5_fill short | 3326 | 49.7% (46.4%, z +2.0), +0.013 ±0.015 | 46.3% (46.2%, z +0.1), -0.030 ±0.027 | 47.3% (46.8%, z +0.5), -0.041 ±0.034 | 47.3% (46.8%, z +0.5), -0.055 ±0.036 | 46.8% (46.5%, z +0.4), -0.079 ±0.049 |
| gap1_cont long | 1717 | 48.6% (50.8%, z -1.0), -0.024 ±0.023 | 54.6% (55.3%, z -0.4), +0.056 ±0.041 | 53.1% (52.7%, z +0.3), +0.068 ±0.050 | 53.0% (51.9%, z +0.8), +0.089 ±0.051 | 53.1% (53.6%, z -0.4), +0.121 ±0.072 |
| gap1_cont short | 1584 | 46.8% (51.0%, z -1.7), -0.030 ±0.024 | 50.3% (50.4%, z -0.1), -0.050 ±0.048 | 51.3% (50.4%, z +0.6), -0.070 ±0.065 | 51.3% (50.9%, z +0.2), -0.051 ±0.070 | 51.6% (49.9%, z +1.3), -0.056 ±0.090 |
| gap1_fill long | 1584 | 51.3% (46.7%, z +1.8), +0.030 ±0.024 | 49.2% (46.1%, z +1.5), +0.050 ±0.048 | 48.5% (47.9%, z +0.4), +0.070 ±0.065 | 48.5% (47.5%, z +0.7), +0.051 ±0.070 | 47.9% (48.3%, z -0.3), +0.056 ±0.090 |
| gap1_fill short | 1717 | 50.6% (46.3%, z +1.9), +0.024 ±0.023 | 45.0% (45.5%, z -0.3), -0.056 ±0.041 | 46.6% (46.8%, z -0.1), -0.068 ±0.050 | 46.8% (47.8%, z -0.8), -0.089 ±0.051 | 46.6% (47.5%, z -0.8), -0.121 ±0.072 |

| Rule | Count | +5m: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|
| first_half_hour long | 3808 | 48.4% (61.9%, z -9.5), -0.003 ±0.011 | 52.0% (65.4%, z -14.6), +0.040 ±0.025 | 53.6% (62.8%, z -13.4), +0.093 ±0.033 |
| first_half_hour short | 3355 | 51.7% (61.5%, z -6.2), +0.025 ±0.013 | 51.1% (62.3%, z -10.7), +0.034 ±0.033 | 50.7% (59.8%, z -11.5), +0.030 ±0.042 |

## spy: SPY only

| Rule | Count | Days | Our way 10m | Ctrl 10m | Gap 10m (z) | Our way 30m | Ctrl 30m | Gap 30m (z) | Avg 10m % | Avg 30m % | Years held | Meets bar | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 220 | 209 | 46.8% ±3.3 | 60.0% | -13.2 (-3.1) | 50.0% ±3.4 | 61.8% | -11.8 (-3.6) | -0.003 ±0.008 | +0.006 ±0.014 | 0/5 | no | FAIL |
| squeeze short, 1m bars | 194 | 176 | 46.9% ±3.7 | 54.1% | -7.2 (-1.5) | 42.3% ±3.4 | 57.2% | -14.9 (-4.3) | +0.003 ±0.011 | -0.004 ±0.017 | 0/5 | no | FAIL |
| squeeze long, 2m bars | 81 | 78 | 49.4% ±5.5 | 69.1% | -19.8 (-2.6) | 45.7% ±5.7 | 69.1% | -23.5 (-3.8) | -0.014 ±0.012 | -0.033 ±0.018 | 0/5 | no | FAIL |
| squeeze short, 2m bars | 73 | 67 | 41.1% ±5.3 | 57.5% | -16.4 (-2.2) | 38.4% ±5.8 | 61.6% | -23.3 (-4.0) | -0.007 ±0.015 | -0.037 ±0.022 | 0/5 | no | FAIL |
| squeeze long, 3m bars | 51 | 50 | 43.1% ±6.9 | 52.9% | -9.8 (-1.1) | 56.9% ±7.1 | 62.7% | -5.9 (-1.1) | -0.011 ±0.013 | -0.000 ±0.031 | 0/5 | no | FAIL |
| squeeze short, 3m bars | 45 | 45 | 44.4% ±7.5 | 60.0% | -15.6 (-1.7) | 57.8% ±7.4 | 71.1% | -13.3 (-1.8) | -0.015 ±0.024 | +0.073 ±0.039 | 0/5 | no | FAIL |
| squeeze long, 4m bars | 37 | 36 | 45.9% ±8.1 | 56.8% | -10.8 (-1.2) | 51.4% ±8.6 | 59.5% | -8.1 (-0.8) | -0.004 ±0.018 | -0.003 ±0.037 | 0/5 | no | FAIL |
| squeeze short, 4m bars | 30 | 28 | 53.3% ±9.9 | 53.3% | +0.0 (+0.0) | 50.0% ±9.3 | 56.7% | -6.7 (-0.7) | +0.064 ±0.035 | +0.045 ±0.033 | 0/5 | no | FAIL |
| squeeze long, 5m bars | 38 | 38 | 50.0% ±8.2 | 57.9% | -7.9 (-0.7) | 50.0% ±8.2 | 57.9% | -7.9 (-1.1) | -0.027 ±0.041 | -0.035 ±0.054 | 0/5 | no | FAIL |
| squeeze short, 5m bars | 43 | 43 | 48.8% ±7.7 | 44.2% | +4.7 (+0.5) | 53.5% ±7.7 | 46.5% | +7.0 (+0.8) | -0.020 ±0.021 | +0.036 ±0.035 | 1/5 | no | FAIL |
| pullback long, 1m bars | 340 | 305 | 52.6% ±2.7 | 58.2% | -5.6 (-1.6) | 53.5% ±2.9 | 58.5% | -5.0 (-2.0) | +0.000 ±0.009 | +0.003 ±0.016 | 0/5 | no | FAIL |
| pullback short, 1m bars | 297 | 242 | 46.5% ±2.9 | 53.2% | -6.7 (-1.9) | 44.4% ±3.1 | 59.6% | -15.2 (-5.7) | -0.009 ±0.009 | -0.005 ±0.015 | 0/5 | no | FAIL |
| pullback long, 2m bars | 123 | 118 | 52.0% ±4.5 | 63.4% | -11.4 (-2.2) | 59.3% ±4.5 | 66.7% | -7.3 (-1.5) | +0.004 ±0.010 | +0.039 ±0.017 | 2/5 | no | FAIL |
| pullback short, 2m bars | 111 | 102 | 37.8% ±4.6 | 55.0% | -17.1 (-2.7) | 44.1% ±4.9 | 57.7% | -13.5 (-3.2) | -0.022 ±0.014 | -0.029 ±0.023 | 0/5 | no | FAIL |
| pullback long, 3m bars | 56 | 53 | 50.0% ±6.9 | 60.7% | -10.7 (-1.6) | 46.4% ±7.1 | 60.7% | -14.3 (-2.4) | -0.000 ±0.013 | +0.002 ±0.023 | 0/5 | no | FAIL |
| pullback short, 3m bars | 42 | 40 | 47.6% ±7.4 | 59.5% | -11.9 (-1.2) | 47.6% ±7.8 | 64.3% | -16.7 (-2.2) | -0.034 ±0.027 | -0.026 ±0.046 | 0/5 | no | FAIL |
| pullback long, 4m bars | 31 | 29 | 58.1% ±9.1 | 51.6% | +6.5 (+0.6) | 45.2% ±9.7 | 45.2% | +0.0 (+0.0) | +0.000 ±0.013 | -0.008 ±0.022 | 0/5 | no | FAIL |
| pullback short, 4m bars | 18 | 17 | 44.4% ±11.4 | 61.1% | -16.7 (-1.4) | 44.4% ±12.6 | 61.1% | -16.7 (-2.0) | -0.042 ±0.039 | -0.015 ±0.098 | 0/5 | no | FAIL |
| pullback long, 5m bars | 18 | 18 | 50.0% ±12.1 | 77.8% | -27.8 (-2.6) | 44.4% ±12.1 | 61.1% | -16.7 (-1.1) | +0.019 ±0.025 | +0.001 ±0.031 | 0/5 | no | FAIL |
| pullback short, 5m bars | 23 | 23 | 34.8% ±10.2 | 47.8% | -13.0 (-1.0) | 56.5% ±10.6 | 73.9% | -17.4 (-1.3) | -0.018 ±0.021 | +0.002 ±0.047 | 0/5 | no | FAIL |
| e1_trend long, 1m bars | 6635 | 1258 | 52.1% ±0.6 | 57.9% | -5.7 (-7.9) | 52.7% ±0.8 | 58.6% | -5.9 (-10.3) | +0.001 ±0.002 | +0.004 ±0.004 | 0/5 | no | FAIL |
| e1_trend short, 1m bars | 6103 | 1253 | 47.7% ±0.6 | 54.4% | -6.7 (-8.7) | 46.8% ±0.8 | 53.5% | -6.8 (-11.4) | -0.003 ±0.002 | -0.006 ±0.004 | 0/5 | no | FAIL |
| e1_trend long, 2m bars | 3311 | 1210 | 51.4% ±0.9 | 59.3% | -7.9 (-7.7) | 52.8% ±1.0 | 60.9% | -8.1 (-9.8) | -0.000 ±0.003 | +0.003 ±0.005 | 0/5 | no | FAIL |
| e1_trend short, 2m bars | 3019 | 1146 | 45.8% ±0.9 | 56.3% | -10.5 (-9.1) | 46.3% ±1.0 | 55.8% | -9.5 (-10.3) | -0.010 ±0.003 | -0.009 ±0.006 | 0/5 | no | FAIL |
| e1_trend long, 3m bars | 2184 | 1076 | 51.3% ±1.1 | 59.6% | -8.2 (-6.5) | 52.3% ±1.1 | 61.2% | -8.9 (-8.8) | -0.001 ±0.003 | +0.007 ±0.007 | 0/5 | no | FAIL |
| e1_trend short, 3m bars | 1947 | 999 | 48.0% ±1.1 | 57.4% | -9.5 (-6.8) | 47.9% ±1.2 | 56.9% | -9.0 (-8.0) | -0.000 ±0.004 | -0.002 ±0.007 | 0/5 | no | FAIL |
| e1_trend long, 4m bars | 1587 | 950 | 49.3% ±1.3 | 60.5% | -11.2 (-6.9) | 49.8% ±1.3 | 60.5% | -10.6 (-8.7) | -0.005 ±0.004 | +0.002 ±0.007 | 0/5 | no | FAIL |
| e1_trend short, 4m bars | 1442 | 876 | 46.8% ±1.3 | 58.3% | -11.5 (-7.1) | 46.6% ±1.4 | 58.5% | -11.9 (-9.3) | -0.005 ±0.005 | -0.013 ±0.008 | 0/5 | no | FAIL |
| e1_trend long, 5m bars | 1423 | 917 | 50.9% ±1.3 | 59.9% | -9.1 (-5.6) | 50.9% ±1.4 | 60.6% | -9.7 (-7.6) | -0.004 ±0.004 | +0.002 ±0.008 | 0/5 | no | FAIL |
| e1_trend short, 5m bars | 1304 | 823 | 47.0% ±1.4 | 58.0% | -11.0 (-6.3) | 47.8% ±1.4 | 56.9% | -9.1 (-7.0) | -0.003 ±0.005 | +0.003 ±0.008 | 0/5 | no | FAIL |
| e1_reject long, 1m bars | 11955 | 1258 | 51.7% ±0.5 | 61.5% | -9.8 (-19.0) | 52.6% ±0.7 | 61.2% | -8.6 (-21.0) | +0.001 ±0.002 | +0.004 ±0.004 | 0/5 | no | FAIL |
| e1_reject short, 1m bars | 10060 | 1249 | 47.4% ±0.5 | 58.3% | -10.9 (-19.5) | 46.8% ±0.7 | 56.4% | -9.5 (-19.7) | -0.001 ±0.002 | -0.003 ±0.004 | 0/5 | no | FAIL |
| e1_reject long, 2m bars | 8915 | 1210 | 50.6% ±0.6 | 61.2% | -10.6 (-17.8) | 52.3% ±0.8 | 60.5% | -8.2 (-17.2) | +0.001 ±0.002 | +0.003 ±0.004 | 0/5 | no | FAIL |
| e1_reject short, 2m bars | 6915 | 1146 | 47.3% ±0.6 | 58.3% | -11.0 (-16.3) | 46.7% ±0.8 | 55.9% | -9.2 (-16.6) | -0.002 ±0.002 | -0.003 ±0.005 | 0/5 | no | FAIL |
| e1_reject long, 3m bars | 6979 | 1110 | 51.6% ±0.7 | 60.9% | -9.3 (-13.4) | 53.2% ±0.9 | 61.0% | -7.7 (-14.1) | +0.002 ±0.002 | +0.006 ±0.004 | 0/5 | no | FAIL |
| e1_reject short, 3m bars | 5217 | 1017 | 47.9% ±0.7 | 57.0% | -9.1 (-11.3) | 46.7% ±0.9 | 55.1% | -8.3 (-13.0) | -0.003 ±0.003 | -0.008 ±0.006 | 0/5 | no | FAIL |
| e1_reject long, 4m bars | 5027 | 1027 | 51.3% ±0.8 | 60.4% | -9.1 (-11.1) | 52.9% ±1.0 | 60.6% | -7.7 (-12.1) | +0.000 ±0.002 | +0.007 ±0.004 | 0/5 | no | FAIL |
| e1_reject short, 4m bars | 3745 | 916 | 47.1% ±0.8 | 57.1% | -10.0 (-10.2) | 46.4% ±1.0 | 55.3% | -8.8 (-11.3) | -0.004 ±0.003 | -0.008 ±0.006 | 0/5 | no | FAIL |
| e1_reject long, 5m bars | 3889 | 946 | 50.5% ±0.8 | 60.1% | -9.6 (-10.6) | 52.6% ±1.0 | 60.0% | -7.4 (-9.9) | +0.000 ±0.002 | +0.005 ±0.005 | 0/5 | no | FAIL |
| e1_reject short, 5m bars | 2862 | 821 | 46.6% ±0.9 | 56.8% | -10.2 (-9.5) | 46.6% ±1.1 | 55.5% | -8.9 (-10.4) | -0.007 ±0.003 | -0.005 ±0.006 | 0/5 | no | FAIL |
| r2_rsi long, 1m bars | 1774 | 824 | 50.2% ±1.2 | 41.8% | +8.3 (+5.8) | 51.8% ±1.4 | 44.5% | +7.3 (+6.5) | -0.007 ±0.005 | -0.008 ±0.009 | 2/5 | no | FAIL |
| r2_rsi short, 1m bars | 1169 | 702 | 46.3% ±1.5 | 39.4% | +6.8 (+4.1) | 45.7% ±1.6 | 39.2% | +6.5 (+4.5) | -0.000 ±0.004 | +0.000 ±0.008 | 2/5 | no | FAIL |
| r2_rsi long, 2m bars | 1111 | 578 | 50.5% ±1.5 | 47.5% | +3.0 (+1.6) | 50.3% ±1.7 | 47.1% | +3.2 (+2.2) | -0.012 ±0.005 | -0.014 ±0.011 | 0/5 | no | FAIL |
| r2_rsi short, 2m bars | 704 | 475 | 45.5% ±1.9 | 49.1% | -3.7 (-1.6) | 46.0% ±2.0 | 46.4% | -0.4 (-0.2) | -0.007 ±0.006 | -0.015 ±0.010 | 0/5 | no | FAIL |
| r2_rsi long, 3m bars | 937 | 469 | 51.2% ±1.7 | 53.0% | -1.8 (-0.9) | 51.0% ±1.9 | 54.9% | -3.8 (-2.6) | -0.008 ±0.006 | -0.009 ±0.011 | 0/5 | no | FAIL |
| r2_rsi short, 3m bars | 525 | 383 | 47.0% ±2.1 | 55.6% | -8.6 (-3.1) | 44.6% ±2.3 | 50.1% | -5.5 (-2.5) | -0.001 ±0.006 | -0.012 ±0.012 | 0/5 | no | FAIL |
| r2_rsi long, 4m bars | 754 | 409 | 51.5% ±1.8 | 56.4% | -4.9 (-2.2) | 51.6% ±2.0 | 55.7% | -4.1 (-2.1) | -0.009 ±0.007 | -0.010 ±0.012 | 0/5 | no | FAIL |
| r2_rsi short, 4m bars | 467 | 362 | 43.9% ±2.3 | 49.3% | -5.4 (-1.9) | 46.5% ±2.4 | 52.2% | -5.8 (-2.4) | -0.002 ±0.007 | -0.003 ±0.013 | 0/5 | no | FAIL |
| r2_rsi long, 5m bars | 675 | 393 | 49.3% ±1.9 | 58.5% | -9.2 (-3.9) | 47.9% ±2.1 | 55.9% | -8.0 (-4.3) | -0.015 ±0.007 | -0.031 ±0.013 | 0/5 | no | FAIL |
| r2_rsi short, 5m bars | 412 | 325 | 47.6% ±2.4 | 55.1% | -7.5 (-2.4) | 44.9% ±2.5 | 54.9% | -10.0 (-4.2) | +0.001 ±0.008 | +0.002 ±0.013 | 0/5 | no | FAIL |
| r2_rsi_sym long, 1m bars | 1020 | 636 | 51.7% ±1.6 | 41.7% | +10.0 (+5.3) | 53.6% ±1.7 | 43.7% | +9.9 (+6.5) | -0.005 ±0.006 | +0.003 ±0.011 | 2/5 | no | FAIL |
| r2_rsi_sym short, 1m bars | 1169 | 702 | 46.3% ±1.5 | 38.9% | +7.4 (+4.1) | 45.7% ±1.6 | 37.1% | +8.6 (+6.0) | -0.000 ±0.004 | +0.000 ±0.008 | 2/5 | no | FAIL |
| r2_rsi_sym long, 2m bars | 582 | 406 | 51.2% ±2.0 | 44.2% | +7.0 (+2.8) | 53.3% ±2.1 | 52.6% | +0.7 (+0.3) | -0.005 ±0.007 | +0.013 ±0.013 | 0/5 | no | FAIL |
| r2_rsi_sym short, 2m bars | 704 | 475 | 45.5% ±1.9 | 45.6% | -0.1 (-0.1) | 46.0% ±2.0 | 46.4% | -0.4 (-0.2) | -0.007 ±0.006 | -0.015 ±0.010 | 1/5 | no | FAIL |
| r2_rsi_sym long, 3m bars | 446 | 335 | 51.3% ±2.4 | 54.3% | -2.9 (-1.0) | 51.1% ±2.5 | 56.7% | -5.6 (-2.3) | -0.011 ±0.010 | -0.014 ±0.013 | 0/5 | no | FAIL |
| r2_rsi_sym short, 3m bars | 525 | 383 | 47.0% ±2.1 | 51.4% | -4.4 (-1.6) | 44.6% ±2.3 | 49.5% | -5.0 (-2.2) | -0.001 ±0.006 | -0.012 ±0.012 | 0/5 | no | FAIL |
| r2_rsi_sym long, 4m bars | 349 | 273 | 52.4% ±2.7 | 53.9% | -1.4 (-0.4) | 51.6% ±2.7 | 58.7% | -7.2 (-2.8) | -0.004 ±0.008 | -0.005 ±0.015 | 0/5 | no | FAIL |
| r2_rsi_sym short, 4m bars | 467 | 362 | 43.9% ±2.3 | 57.8% | -13.9 (-4.9) | 46.5% ±2.4 | 54.6% | -8.1 (-3.6) | -0.002 ±0.007 | -0.003 ±0.013 | 0/5 | no | FAIL |
| r2_rsi_sym long, 5m bars | 315 | 260 | 52.4% ±2.8 | 57.1% | -4.8 (-1.4) | 50.2% ±2.9 | 56.8% | -6.7 (-2.5) | -0.010 ±0.011 | -0.016 ±0.017 | 0/5 | no | FAIL |
| r2_rsi_sym short, 5m bars | 412 | 325 | 47.6% ±2.4 | 60.7% | -13.1 (-4.3) | 44.9% ±2.5 | 55.6% | -10.7 (-4.3) | +0.001 ±0.008 | +0.002 ±0.013 | 0/5 | no | FAIL |
| b3_touch long, 1m bars | 11219 | 1257 | 52.1% ±0.5 | 41.5% | +10.6 (+20.0) | 53.4% ±0.7 | 44.0% | +9.5 (+21.9) | +0.003 ±0.002 | +0.005 ±0.004 | 4/5 | yes | PASS |
| b3_touch short, 1m bars | 12487 | 1257 | 47.5% ±0.5 | 38.2% | +9.3 (+17.9) | 46.8% ±0.7 | 38.9% | +7.9 (+19.6) | -0.001 ±0.001 | -0.003 ±0.003 | 0/5 | no | FAIL |
| b3_touch long, 2m bars | 8334 | 1237 | 53.0% ±0.6 | 41.0% | +12.0 (+18.8) | 53.6% ±0.8 | 43.9% | +9.6 (+19.1) | +0.003 ±0.002 | +0.006 ±0.004 | 3/5 | no | FAIL |
| b3_touch short, 2m bars | 9403 | 1247 | 48.4% ±0.6 | 37.7% | +10.7 (+18.6) | 46.8% ±0.8 | 38.2% | +8.6 (+18.1) | -0.001 ±0.002 | -0.003 ±0.004 | 0/5 | no | FAIL |
| b3_touch long, 3m bars | 6694 | 1140 | 52.7% ±0.7 | 41.5% | +11.2 (+15.2) | 53.6% ±0.9 | 45.2% | +8.5 (+15.0) | +0.002 ±0.002 | +0.004 ±0.005 | 3/5 | no | FAIL |
| b3_touch short, 3m bars | 7596 | 1187 | 48.0% ±0.7 | 38.9% | +9.1 (+14.1) | 46.9% ±0.9 | 39.8% | +7.1 (+13.1) | -0.002 ±0.002 | -0.005 ±0.004 | 1/5 | no | FAIL |
| b3_touch long, 4m bars | 4598 | 1054 | 53.5% ±0.8 | 44.2% | +9.2 (+11.1) | 53.7% ±1.0 | 46.7% | +7.0 (+10.0) | +0.003 ±0.003 | +0.006 ±0.006 | 3/5 | no | FAIL |
| b3_touch short, 4m bars | 5275 | 1106 | 47.4% ±0.8 | 40.3% | +7.1 (+8.9) | 47.0% ±1.0 | 40.7% | +6.3 (+9.5) | -0.004 ±0.002 | -0.008 ±0.005 | 0/5 | no | FAIL |
| b3_touch long, 5m bars | 3682 | 975 | 51.7% ±0.8 | 42.6% | +9.2 (+10.2) | 53.3% ±1.1 | 46.5% | +6.8 (+9.3) | +0.000 ±0.003 | +0.003 ±0.006 | 3/5 | no | FAIL |
| b3_touch short, 5m bars | 4225 | 1029 | 48.1% ±0.8 | 40.4% | +7.7 (+9.0) | 46.9% ±1.0 | 40.3% | +6.7 (+9.5) | -0.003 ±0.002 | -0.007 ±0.005 | 1/5 | no | FAIL |
| b3_reentry long, 1m bars | 3850 | 1215 | 53.5% ±0.8 | 39.0% | +14.5 (+15.1) | 53.8% ±0.9 | 42.2% | +11.7 (+15.2) | +0.006 ±0.003 | +0.010 ±0.006 | 5/5 | yes | PASS |
| b3_reentry short, 1m bars | 3714 | 1220 | 47.9% ±0.8 | 37.3% | +10.6 (+11.5) | 46.2% ±0.9 | 37.8% | +8.4 (+10.8) | -0.001 ±0.003 | -0.003 ±0.005 | 2/5 | no | FAIL |
| b3_reentry long, 2m bars | 2184 | 1050 | 52.7% ±1.1 | 40.3% | +12.4 (+9.4) | 52.1% ±1.2 | 40.9% | +11.1 (+10.4) | -0.002 ±0.004 | +0.003 ±0.007 | 2/5 | no | FAIL |
| b3_reentry short, 2m bars | 2119 | 1060 | 48.2% ±1.1 | 37.8% | +10.4 (+8.0) | 46.1% ±1.2 | 36.8% | +9.3 (+9.0) | -0.001 ±0.003 | -0.007 ±0.006 | 0/5 | no | FAIL |
| b3_reentry long, 3m bars | 1552 | 891 | 49.8% ±1.3 | 44.3% | +5.5 (+3.6) | 52.1% ±1.4 | 46.1% | +6.0 (+5.1) | -0.004 ±0.004 | -0.001 ±0.008 | 2/5 | no | FAIL |
| b3_reentry short, 3m bars | 1546 | 916 | 46.8% ±1.3 | 42.2% | +4.6 (+3.0) | 45.7% ±1.4 | 40.8% | +4.9 (+3.9) | -0.003 ±0.004 | -0.011 ±0.008 | 0/5 | no | FAIL |
| b3_reentry long, 4m bars | 1154 | 772 | 51.1% ±1.5 | 44.0% | +7.1 (+4.2) | 53.2% ±1.6 | 49.7% | +3.5 (+2.6) | -0.003 ±0.006 | +0.009 ±0.010 | 2/5 | no | FAIL |
| b3_reentry short, 4m bars | 1165 | 804 | 46.4% ±1.5 | 40.5% | +5.9 (+3.3) | 46.7% ±1.6 | 43.2% | +3.5 (+2.5) | -0.005 ±0.005 | -0.006 ±0.009 | 2/5 | no | FAIL |
| b3_reentry long, 5m bars | 1012 | 735 | 51.3% ±1.6 | 47.0% | +4.2 (+2.2) | 53.3% ±1.6 | 48.7% | +4.5 (+3.1) | -0.004 ±0.007 | +0.009 ±0.011 | 2/5 | no | FAIL |
| b3_reentry short, 5m bars | 1061 | 772 | 46.0% ±1.5 | 41.4% | +4.6 (+2.5) | 47.6% ±1.6 | 43.8% | +3.8 (+2.6) | -0.002 ±0.005 | -0.004 ±0.009 | 1/5 | no | FAIL |
| orb15 long, 1m bars | 472 | 472 | 52.1% ±2.3 | 67.8% | -15.7 (-5.7) | 58.5% ±2.3 | 66.1% | -7.6 (-3.3) | +0.010 ±0.008 | +0.026 ±0.012 | 0/5 | no | FAIL |
| orb15 short, 1m bars | 452 | 452 | 46.7% ±2.3 | 64.6% | -17.9 (-6.1) | 47.3% ±2.4 | 64.2% | -16.8 (-6.8) | -0.019 ±0.010 | -0.002 ±0.015 | 0/5 | no | FAIL |
| orb15 long, 5m bars | 107 | 107 | 50.5% ±4.9 | 65.4% | -15.0 (-2.5) | 56.1% ±4.8 | 64.5% | -8.4 (-1.5) | -0.005 ±0.024 | +0.013 ±0.024 | 0/5 | no | FAIL |
| orb15 short, 5m bars | 144 | 144 | 53.5% ±4.2 | 66.0% | -12.5 (-2.4) | 52.8% ±4.2 | 66.7% | -13.9 (-3.5) | +0.009 ±0.018 | +0.026 ±0.030 | 0/5 | no | FAIL |
| orb30 long, 1m bars | 432 | 432 | 49.8% ±2.4 | 63.7% | -13.9 (-4.7) | 56.0% ±2.4 | 60.0% | -3.9 (-1.5) | +0.002 ±0.008 | +0.023 ±0.011 | 0/5 | no | FAIL |
| orb30 short, 1m bars | 439 | 439 | 45.1% ±2.4 | 64.2% | -19.1 (-6.1) | 46.5% ±2.4 | 62.4% | -15.9 (-6.5) | -0.010 ±0.007 | +0.004 ±0.013 | 0/5 | no | FAIL |
| orb30 long, 5m bars | 123 | 123 | 56.1% ±4.5 | 58.5% | -2.4 (-0.4) | 57.7% ±4.5 | 61.8% | -4.1 (-1.0) | -0.012 ±0.018 | +0.010 ±0.021 | 0/5 | no | FAIL |
| orb30 short, 5m bars | 154 | 154 | 53.9% ±4.0 | 67.5% | -13.6 (-2.7) | 47.4% ±4.0 | 70.8% | -23.4 (-5.9) | +0.013 ±0.015 | +0.020 ±0.025 | 0/5 | no | FAIL |
| gap0.5_cont long | 246 | 246 | 50.0% ±3.2 | 51.6% | -1.6 (-0.4) | 54.5% ±3.2 | 56.1% | -1.6 (-0.5) | -0.016 ±0.018 | +0.029 ±0.026 | 1/5 | no | FAIL |
| gap0.5_cont short | 207 | 207 | 57.0% ±3.4 | 52.7% | +4.3 (+1.0) | 61.4% ±3.4 | 51.2% | +10.1 (+3.0) | +0.043 ±0.016 | +0.090 ±0.030 | 2/5 | no | FAIL |
| gap0.5_fill long | 207 | 207 | 41.5% ±3.4 | 44.4% | -2.9 (-0.6) | 38.6% ±3.4 | 47.8% | -9.2 (-2.6) | -0.043 ±0.016 | -0.090 ±0.030 | 0/5 | no | FAIL |
| gap0.5_fill short | 246 | 246 | 49.6% ±3.2 | 43.5% | +6.1 (+1.5) | 45.5% ±3.2 | 45.1% | +0.4 (+0.1) | +0.016 ±0.018 | -0.029 ±0.026 | 1/5 | no | FAIL |
| gap1_cont long | 73 | 73 | 54.8% ±5.9 | 63.0% | -8.2 (-1.1) | 64.4% ±5.6 | 63.0% | +1.4 (+0.3) | -0.019 ±0.047 | +0.121 ±0.062 | 1/5 | no | FAIL |
| gap1_cont short | 83 | 83 | 53.0% ±5.5 | 54.2% | -1.2 (-0.2) | 66.3% ±5.2 | 49.4% | +16.9 (+2.7) | +0.044 ±0.026 | +0.111 ±0.061 | 2/5 | no | FAIL |
| gap1_fill long | 83 | 83 | 44.6% ±5.5 | 39.8% | +4.8 (+0.6) | 33.7% ±5.2 | 45.8% | -12.0 (-2.2) | -0.044 ±0.026 | -0.111 ±0.061 | 0/5 | no | FAIL |
| gap1_fill short | 73 | 73 | 43.8% ±5.8 | 37.0% | +6.8 (+0.9) | 35.6% ±5.6 | 30.1% | +5.5 (+0.9) | +0.019 ±0.047 | -0.121 ±0.062 | 0/5 | no | FAIL |
| first_half_hour long | 181 | 181 | 54.1% ±3.7 | 79.6% | -25.4 (-6.1) | 56.4% ±3.7 | 75.7% | -19.3 (-5.2) | +0.009 ±0.020 | +0.022 ±0.027 | 0/5 | no | FAIL |
| first_half_hour short | 169 | 169 | 50.3% ±3.9 | 70.4% | -20.1 (-4.2) | 45.0% ±3.8 | 62.7% | -17.8 (-4.7) | -0.012 ±0.023 | -0.056 ±0.035 | 0/5 | no | FAIL |

Gap and first-half-hour rules at their extra horizons (control over the same number of minutes):

| Rule | Count | +5m: our way (ctrl), avg % | to 10:00: our way (ctrl), avg % | to 10:30: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|---|---|
| gap0.5_cont long | 246 | 48.8% (52.4%, z -0.9), -0.021 ±0.013 | 53.7% (54.1%, z -0.1), -0.002 ±0.025 | 55.7% (54.9%, z +0.3), +0.042 ±0.031 | 57.3% (54.1%, z +1.3), +0.054 ±0.032 | 58.5% (61.4%, z -1.3), +0.074 ±0.048 |
| gap0.5_cont short | 207 | 47.3% (51.2%, z -0.8), +0.003 ±0.013 | 56.0% (52.7%, z +0.8), +0.022 ±0.028 | 51.7% (51.2%, z +0.1), +0.032 ±0.039 | 55.1% (48.3%, z +2.2), +0.027 ±0.044 | 52.2% (47.8%, z +1.8), +0.025 ±0.061 |
| gap0.5_fill long | 207 | 50.7% (45.4%, z +1.1), -0.003 ±0.013 | 44.0% (44.9%, z -0.2), -0.022 ±0.028 | 48.3% (51.2%, z -0.9), -0.032 ±0.039 | 44.9% (48.8%, z -1.3), -0.027 ±0.044 | 47.8% (49.3%, z -0.7), -0.025 ±0.061 |
| gap0.5_fill short | 246 | 50.4% (46.7%, z +0.8), +0.021 ±0.013 | 45.9% (48.8%, z -0.8), +0.002 ±0.025 | 44.3% (39.8%, z +1.6), -0.042 ±0.031 | 42.7% (40.2%, z +0.9), -0.054 ±0.032 | 41.1% (37.4%, z +1.8), -0.074 ±0.048 |
| gap1_cont long | 73 | 50.7% (56.2%, z -0.8), -0.044 ±0.031 | 61.6% (69.9%, z -1.4), +0.058 ±0.066 | 58.9% (65.8%, z -1.5), +0.163 ±0.070 | 60.3% (65.8%, z -1.2), +0.160 ±0.073 | 65.8% (67.1%, z -0.4), +0.155 ±0.123 |
| gap1_cont short | 83 | 44.6% (53.0%, z -1.1), -0.017 ±0.025 | 54.2% (48.2%, z +1.0), -0.032 ±0.055 | 57.8% (50.6%, z +1.5), +0.064 ±0.073 | 60.2% (54.2%, z +1.2), +0.024 ±0.084 | 55.4% (48.2%, z +1.6), -0.013 ±0.121 |
| gap1_fill long | 83 | 51.8% (37.3%, z +1.8), +0.017 ±0.025 | 45.8% (44.6%, z +0.2), +0.032 ±0.055 | 42.2% (44.6%, z -0.5), -0.064 ±0.073 | 39.8% (45.8%, z -1.7), -0.024 ±0.084 | 44.6% (49.4%, z -1.2), +0.013 ±0.121 |
| gap1_fill short | 73 | 49.3% (32.9%, z +2.1), +0.044 ±0.031 | 37.0% (32.9%, z +0.7), -0.058 ±0.066 | 41.1% (37.0%, z +0.8), -0.163 ±0.070 | 39.7% (35.6%, z +1.0), -0.160 ±0.073 | 34.2% (35.6%, z -0.4), -0.155 ±0.123 |

| Rule | Count | +5m: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|
| first_half_hour long | 181 | 51.9% (74.0%, z -4.7), -0.006 ±0.017 | 56.9% (72.9%, z -5.9), +0.056 ±0.036 | 58.0% (71.3%, z -5.2), +0.104 ±0.050 |
| first_half_hour short | 169 | 50.9% (63.9%, z -2.5), +0.005 ±0.021 | 47.3% (63.3%, z -4.4), -0.034 ±0.047 | 49.1% (58.0%, z -3.0), -0.031 ±0.066 |

## atr_pick: the ATR % pick (comparison with earlier tests)

| Rule | Count | Days | Our way 10m | Ctrl 10m | Gap 10m (z) | Our way 30m | Ctrl 30m | Gap 30m (z) | Avg 10m % | Avg 30m % | Years held | Meets bar | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 291 | 255 | 50.2% ±2.8 | 61.5% | -11.3 (-3.2) | 48.1% ±3.0 | 57.7% | -9.6 (-3.4) | +0.027 ±0.021 | -0.026 ±0.037 | 0/5 | no | (comparison only) |
| squeeze short, 1m bars | 277 | 254 | 50.5% ±3.0 | 64.6% | -14.1 (-3.7) | 48.0% ±3.0 | 62.5% | -14.4 (-4.9) | +0.054 ±0.031 | +0.084 ±0.046 | 0/5 | no | (comparison only) |
| squeeze long, 2m bars | 96 | 90 | 58.3% ±4.8 | 67.7% | -9.4 (-1.6) | 60.4% ±5.1 | 72.9% | -12.5 (-2.6) | +0.082 ±0.038 | +0.191 ±0.089 | 0/5 | no | (comparison only) |
| squeeze short, 2m bars | 95 | 89 | 48.4% ±5.2 | 66.3% | -17.9 (-2.7) | 45.3% ±5.3 | 70.5% | -25.3 (-5.0) | +0.048 ±0.034 | +0.090 ±0.076 | 0/5 | no | (comparison only) |
| squeeze long, 3m bars | 74 | 70 | 58.1% ±5.7 | 55.4% | +2.7 (+0.4) | 59.5% ±6.0 | 66.2% | -6.8 (-1.5) | +0.128 ±0.059 | +0.184 ±0.117 | 0/5 | no | (comparison only) |
| squeeze short, 3m bars | 78 | 74 | 56.4% ±5.9 | 59.0% | -2.6 (-0.3) | 55.1% ±5.8 | 57.7% | -2.6 (-0.4) | -0.051 ±0.098 | +0.032 ±0.111 | 2/5 | no | (comparison only) |
| squeeze long, 4m bars | 83 | 79 | 47.0% ±5.6 | 53.0% | -6.0 (-0.9) | 44.6% ±5.5 | 48.2% | -3.6 (-0.7) | +0.002 ±0.076 | -0.024 ±0.106 | 0/5 | no | (comparison only) |
| squeeze short, 4m bars | 66 | 65 | 51.5% ±6.3 | 48.5% | +3.0 (+0.4) | 57.6% ±6.2 | 65.2% | -7.6 (-1.1) | -0.122 ±0.105 | +0.155 ±0.144 | 0/5 | no | (comparison only) |
| squeeze long, 5m bars | 93 | 86 | 49.5% ±5.0 | 62.4% | -12.9 (-2.1) | 47.3% ±5.5 | 47.3% | +0.0 (+0.0) | +0.039 ±0.072 | +0.027 ±0.114 | 1/5 | no | (comparison only) |
| squeeze short, 5m bars | 93 | 89 | 49.5% ±5.3 | 50.5% | -1.1 (-0.2) | 47.3% ±5.3 | 51.6% | -4.3 (-0.7) | +0.017 ±0.080 | +0.142 ±0.141 | 1/5 | no | (comparison only) |
| pullback long, 1m bars | 365 | 306 | 51.5% ±2.6 | 61.1% | -9.6 (-3.3) | 52.9% ±2.6 | 61.1% | -8.2 (-3.2) | +0.031 ±0.023 | +0.054 ±0.038 | 0/5 | no | (comparison only) |
| pullback short, 1m bars | 272 | 238 | 52.2% ±3.0 | 63.2% | -11.0 (-3.1) | 52.6% ±3.1 | 55.5% | -2.9 (-1.0) | +0.032 ±0.022 | +0.069 ±0.038 | 0/5 | no | (comparison only) |
| pullback long, 2m bars | 137 | 127 | 51.1% ±4.3 | 63.5% | -12.4 (-2.3) | 51.8% ±4.4 | 67.2% | -15.3 (-3.3) | +0.044 ±0.037 | +0.035 ±0.069 | 0/5 | no | (comparison only) |
| pullback short, 2m bars | 108 | 105 | 44.4% ±4.8 | 63.0% | -18.5 (-3.4) | 50.0% ±5.0 | 58.3% | -8.3 (-2.1) | -0.015 ±0.049 | +0.079 ±0.064 | 0/5 | no | (comparison only) |
| pullback long, 3m bars | 84 | 82 | 50.0% ±5.5 | 60.7% | -10.7 (-1.6) | 53.6% ±5.6 | 67.9% | -14.3 (-3.2) | +0.101 ±0.064 | +0.039 ±0.108 | 0/5 | no | (comparison only) |
| pullback short, 3m bars | 74 | 72 | 54.1% ±5.8 | 62.2% | -8.1 (-1.2) | 51.4% ±6.0 | 63.5% | -12.2 (-2.4) | -0.029 ±0.067 | +0.041 ±0.120 | 0/5 | no | (comparison only) |
| pullback long, 4m bars | 58 | 55 | 51.7% ±6.6 | 60.3% | -8.6 (-1.1) | 51.7% ±6.4 | 60.3% | -8.6 (-1.7) | +0.018 ±0.094 | +0.089 ±0.129 | 0/5 | no | (comparison only) |
| pullback short, 4m bars | 72 | 70 | 56.9% ±5.9 | 58.3% | -1.4 (-0.2) | 61.1% ±6.0 | 55.6% | +5.6 (+0.9) | +0.196 ±0.072 | +0.348 ±0.120 | 2/5 | no | (comparison only) |
| pullback long, 5m bars | 65 | 60 | 49.2% ±6.0 | 53.8% | -4.6 (-0.7) | 53.8% ±6.7 | 56.9% | -3.1 (-0.5) | -0.027 ±0.084 | -0.010 ±0.127 | 0/5 | no | (comparison only) |
| pullback short, 5m bars | 76 | 70 | 57.9% ±5.8 | 72.4% | -14.5 (-2.2) | 56.6% ±5.8 | 61.8% | -5.3 (-1.0) | +0.124 ±0.060 | +0.232 ±0.149 | 0/5 | no | (comparison only) |
| e1_trend long, 1m bars | 6468 | 1257 | 51.1% ±0.6 | 56.8% | -5.7 (-7.8) | 51.1% ±0.8 | 57.6% | -6.5 (-10.9) | +0.008 ±0.005 | +0.019 ±0.012 | 0/5 | no | (comparison only) |
| e1_trend short, 1m bars | 6291 | 1254 | 49.4% ±0.6 | 57.0% | -7.6 (-10.3) | 49.3% ±0.8 | 55.8% | -6.4 (-11.0) | +0.006 ±0.006 | +0.014 ±0.012 | 0/5 | no | (comparison only) |
| e1_trend long, 2m bars | 3201 | 1188 | 49.5% ±0.9 | 56.5% | -7.0 (-6.5) | 49.7% ±1.0 | 58.5% | -8.7 (-10.2) | -0.000 ±0.007 | +0.006 ±0.014 | 0/5 | no | (comparison only) |
| e1_trend short, 2m bars | 3095 | 1167 | 49.7% ±0.9 | 57.0% | -7.3 (-6.7) | 48.6% ±1.0 | 57.3% | -8.7 (-9.8) | -0.003 ±0.008 | +0.005 ±0.015 | 0/5 | no | (comparison only) |
| e1_trend long, 3m bars | 2080 | 1054 | 49.7% ±1.1 | 59.2% | -9.5 (-7.4) | 49.7% ±1.2 | 58.9% | -9.3 (-8.7) | -0.002 ±0.009 | -0.001 ±0.016 | 0/5 | no | (comparison only) |
| e1_trend short, 3m bars | 1998 | 1029 | 48.6% ±1.1 | 57.5% | -8.9 (-6.4) | 49.1% ±1.2 | 58.2% | -9.1 (-8.7) | -0.002 ±0.010 | -0.001 ±0.019 | 0/5 | no | (comparison only) |
| e1_trend long, 4m bars | 1521 | 935 | 50.5% ±1.3 | 59.4% | -8.9 (-5.6) | 49.1% ±1.3 | 59.4% | -10.3 (-8.8) | -0.003 ±0.010 | -0.015 ±0.019 | 0/5 | no | (comparison only) |
| e1_trend short, 4m bars | 1458 | 885 | 49.4% ±1.3 | 59.2% | -9.8 (-6.3) | 48.1% ±1.4 | 59.8% | -11.7 (-9.5) | +0.016 ±0.012 | +0.001 ±0.022 | 0/5 | no | (comparison only) |
| e1_trend long, 5m bars | 1377 | 872 | 50.1% ±1.3 | 59.9% | -9.8 (-5.8) | 50.3% ±1.4 | 60.6% | -10.3 (-7.3) | -0.005 ±0.014 | -0.003 ±0.022 | 0/5 | no | (comparison only) |
| e1_trend short, 5m bars | 1348 | 841 | 49.0% ±1.4 | 59.1% | -10.1 (-6.0) | 49.1% ±1.3 | 56.8% | -7.6 (-5.8) | +0.001 ±0.014 | -0.007 ±0.024 | 0/5 | no | (comparison only) |
| e1_reject long, 1m bars | 10360 | 1255 | 50.1% ±0.5 | 59.3% | -9.1 (-16.7) | 51.2% ±0.7 | 58.8% | -7.6 (-17.3) | +0.009 ±0.005 | +0.023 ±0.011 | 0/5 | no | (comparison only) |
| e1_reject short, 1m bars | 9570 | 1253 | 49.0% ±0.6 | 58.9% | -9.9 (-16.8) | 49.5% ±0.7 | 57.5% | -8.0 (-17.2) | +0.007 ±0.005 | +0.016 ±0.012 | 0/5 | no | (comparison only) |
| e1_reject long, 2m bars | 7137 | 1182 | 49.8% ±0.7 | 59.2% | -9.4 (-13.3) | 50.7% ±0.9 | 59.3% | -8.6 (-15.3) | +0.007 ±0.006 | +0.022 ±0.012 | 0/5 | no | (comparison only) |
| e1_reject short, 2m bars | 6232 | 1142 | 49.5% ±0.7 | 58.7% | -9.2 (-12.9) | 49.2% ±0.9 | 58.1% | -8.9 (-14.7) | +0.014 ±0.006 | +0.017 ±0.013 | 0/5 | no | (comparison only) |
| e1_reject long, 3m bars | 5309 | 1065 | 50.3% ±0.7 | 57.6% | -7.3 (-9.2) | 50.3% ±1.0 | 57.8% | -7.5 (-11.7) | +0.002 ±0.006 | +0.013 ±0.013 | 0/5 | no | (comparison only) |
| e1_reject short, 3m bars | 4708 | 1005 | 48.3% ±0.8 | 56.6% | -8.3 (-9.7) | 47.7% ±1.0 | 55.8% | -8.1 (-11.8) | -0.005 ±0.007 | -0.004 ±0.015 | 0/5 | no | (comparison only) |
| e1_reject long, 4m bars | 3929 | 971 | 49.7% ±0.8 | 57.3% | -7.7 (-7.9) | 50.1% ±1.0 | 57.9% | -7.8 (-10.9) | +0.001 ±0.007 | +0.008 ±0.013 | 0/5 | no | (comparison only) |
| e1_reject short, 4m bars | 3370 | 899 | 48.3% ±0.9 | 56.2% | -7.9 (-7.4) | 48.6% ±1.1 | 56.5% | -7.9 (-9.6) | +0.004 ±0.008 | +0.011 ±0.016 | 0/5 | no | (comparison only) |
| e1_reject long, 5m bars | 3018 | 882 | 50.1% ±0.9 | 59.7% | -9.7 (-9.2) | 51.0% ±1.1 | 59.6% | -8.5 (-9.9) | +0.002 ±0.008 | +0.022 ±0.015 | 0/5 | no | (comparison only) |
| e1_reject short, 5m bars | 2647 | 818 | 49.8% ±1.0 | 56.7% | -6.8 (-6.2) | 49.1% ±1.1 | 57.0% | -7.8 (-9.1) | +0.000 ±0.009 | +0.021 ±0.018 | 0/5 | no | (comparison only) |
| r2_rsi long, 1m bars | 1689 | 825 | 51.3% ±1.2 | 40.2% | +11.1 (+7.7) | 51.1% ±1.4 | 42.5% | +8.6 (+7.3) | -0.018 ±0.014 | -0.000 ±0.025 | 3/5 | no | (comparison only) |
| r2_rsi short, 1m bars | 1060 | 643 | 47.6% ±1.5 | 40.9% | +6.7 (+3.8) | 46.8% ±1.7 | 42.2% | +4.6 (+3.4) | -0.024 ±0.014 | -0.036 ±0.025 | 2/5 | no | (comparison only) |
| r2_rsi long, 2m bars | 1093 | 622 | 48.2% ±1.5 | 46.4% | +1.8 (+1.0) | 50.4% ±1.7 | 45.4% | +5.0 (+3.5) | -0.033 ±0.019 | -0.004 ±0.032 | 1/5 | no | (comparison only) |
| r2_rsi short, 2m bars | 667 | 459 | 48.6% ±1.9 | 44.7% | +3.9 (+1.7) | 46.3% ±2.1 | 46.6% | -0.3 (-0.2) | -0.044 ±0.020 | -0.064 ±0.035 | 0/5 | no | (comparison only) |
| r2_rsi long, 3m bars | 923 | 526 | 50.5% ±1.7 | 51.8% | -1.3 (-0.7) | 51.4% ±1.8 | 53.0% | -1.6 (-1.0) | -0.010 ±0.017 | -0.002 ±0.031 | 1/5 | no | (comparison only) |
| r2_rsi short, 3m bars | 516 | 392 | 45.3% ±2.2 | 52.5% | -7.2 (-2.7) | 45.5% ±2.2 | 48.6% | -3.1 (-1.5) | -0.044 ±0.022 | -0.073 ±0.040 | 0/5 | no | (comparison only) |
| r2_rsi long, 4m bars | 758 | 464 | 49.2% ±1.7 | 52.5% | -3.3 (-1.5) | 51.3% ±1.9 | 51.8% | -0.5 (-0.3) | -0.038 ±0.021 | -0.011 ±0.033 | 0/5 | no | (comparison only) |
| r2_rsi short, 4m bars | 435 | 373 | 46.7% ±2.4 | 58.2% | -11.5 (-4.0) | 49.2% ±2.4 | 54.7% | -5.5 (-2.4) | -0.013 ±0.024 | -0.021 ±0.042 | 0/5 | no | (comparison only) |
| r2_rsi long, 5m bars | 674 | 446 | 48.7% ±1.9 | 57.3% | -8.6 (-3.7) | 51.9% ±2.0 | 59.3% | -7.4 (-4.2) | -0.025 ±0.019 | -0.001 ±0.033 | 1/5 | no | (comparison only) |
| r2_rsi short, 5m bars | 383 | 340 | 45.2% ±2.5 | 60.3% | -15.1 (-4.9) | 50.4% ±2.5 | 58.2% | -7.8 (-3.2) | -0.046 ±0.023 | -0.014 ±0.037 | 0/5 | no | (comparison only) |
| r2_rsi_sym long, 1m bars | 942 | 599 | 50.3% ±1.7 | 39.0% | +11.4 (+5.7) | 51.1% ±1.8 | 42.0% | +9.0 (+6.4) | -0.026 ±0.021 | +0.010 ±0.037 | 1/5 | no | (comparison only) |
| r2_rsi_sym short, 1m bars | 1060 | 643 | 47.6% ±1.5 | 40.2% | +7.5 (+4.0) | 46.8% ±1.7 | 42.5% | +4.3 (+3.0) | -0.024 ±0.014 | -0.036 ±0.025 | 2/5 | no | (comparison only) |
| r2_rsi_sym long, 2m bars | 595 | 436 | 49.6% ±2.1 | 47.9% | +1.7 (+0.7) | 52.3% ±2.1 | 48.7% | +3.5 (+1.9) | -0.017 ±0.024 | +0.019 ±0.044 | 2/5 | no | (comparison only) |
| r2_rsi_sym short, 2m bars | 667 | 459 | 48.6% ±1.9 | 46.0% | +2.5 (+1.1) | 46.3% ±2.1 | 45.3% | +1.0 (+0.6) | -0.044 ±0.020 | -0.064 ±0.035 | 0/5 | no | (comparison only) |
| r2_rsi_sym long, 3m bars | 465 | 365 | 49.2% ±2.3 | 50.5% | -1.3 (-0.5) | 54.2% ±2.3 | 50.1% | +4.1 (+1.8) | -0.018 ±0.023 | +0.024 ±0.037 | 0/5 | no | (comparison only) |
| r2_rsi_sym short, 3m bars | 516 | 392 | 45.3% ±2.2 | 47.3% | -1.9 (-0.7) | 45.5% ±2.2 | 48.1% | -2.5 (-1.2) | -0.044 ±0.022 | -0.073 ±0.040 | 0/5 | no | (comparison only) |
| r2_rsi_sym long, 4m bars | 384 | 314 | 51.0% ±2.5 | 55.7% | -4.7 (-1.4) | 51.8% ±2.5 | 56.0% | -4.2 (-1.7) | -0.043 ±0.036 | -0.010 ±0.047 | 0/5 | no | (comparison only) |
| r2_rsi_sym short, 4m bars | 435 | 373 | 46.7% ±2.4 | 53.8% | -7.1 (-2.4) | 49.2% ±2.4 | 59.3% | -10.1 (-4.3) | -0.013 ±0.024 | -0.021 ±0.042 | 0/5 | no | (comparison only) |
| r2_rsi_sym long, 5m bars | 349 | 293 | 50.7% ±2.7 | 56.4% | -5.7 (-1.7) | 54.7% ±2.7 | 58.2% | -3.4 (-1.3) | -0.013 ±0.027 | +0.031 ±0.041 | 0/5 | no | (comparison only) |
| r2_rsi_sym short, 5m bars | 383 | 340 | 45.2% ±2.5 | 54.0% | -8.9 (-2.8) | 50.4% ±2.5 | 54.3% | -3.9 (-1.6) | -0.046 ±0.023 | -0.014 ±0.037 | 0/5 | no | (comparison only) |
| b3_touch long, 1m bars | 9476 | 1257 | 49.8% ±0.5 | 39.4% | +10.4 (+17.2) | 50.6% ±0.7 | 41.0% | +9.5 (+20.2) | -0.000 ±0.005 | -0.005 ±0.010 | 1/5 | no | (comparison only) |
| b3_touch short, 1m bars | 9772 | 1258 | 48.0% ±0.5 | 38.7% | +9.3 (+16.2) | 48.0% ±0.7 | 39.5% | +8.5 (+18.2) | -0.009 ±0.004 | -0.017 ±0.009 | 0/5 | no | (comparison only) |
| b3_touch long, 2m bars | 6509 | 1204 | 50.1% ±0.7 | 38.9% | +11.2 (+15.4) | 51.1% ±0.8 | 39.5% | +11.6 (+19.2) | -0.007 ±0.006 | -0.008 ±0.012 | 1/5 | no | (comparison only) |
| b3_touch short, 2m bars | 6640 | 1221 | 48.7% ±0.7 | 37.1% | +11.6 (+15.9) | 48.6% ±0.9 | 39.1% | +9.6 (+16.0) | -0.011 ±0.006 | -0.017 ±0.012 | 1/5 | no | (comparison only) |
| b3_touch long, 3m bars | 5289 | 1109 | 49.6% ±0.8 | 38.9% | +10.7 (+13.5) | 51.0% ±1.0 | 41.4% | +9.6 (+14.7) | -0.009 ±0.008 | +0.001 ±0.015 | 2/5 | no | (comparison only) |
| b3_touch short, 3m bars | 5479 | 1136 | 48.0% ±0.8 | 38.5% | +9.5 (+12.2) | 47.8% ±1.0 | 40.1% | +7.7 (+12.0) | -0.013 ±0.008 | -0.028 ±0.017 | 0/5 | no | (comparison only) |
| b3_touch long, 4m bars | 3776 | 1000 | 49.0% ±0.8 | 40.8% | +8.2 (+9.0) | 50.0% ±1.1 | 43.6% | +6.4 (+8.6) | -0.016 ±0.009 | -0.008 ±0.019 | 1/5 | no | (comparison only) |
| b3_touch short, 4m bars | 3908 | 1041 | 48.9% ±0.9 | 38.9% | +9.9 (+10.8) | 47.8% ±1.1 | 40.5% | +7.3 (+10.2) | -0.006 ±0.009 | -0.023 ±0.018 | 0/5 | no | (comparison only) |
| b3_touch long, 5m bars | 3184 | 918 | 50.7% ±0.9 | 42.7% | +8.1 (+8.2) | 50.5% ±1.1 | 43.5% | +7.0 (+8.7) | +0.002 ±0.010 | +0.002 ±0.021 | 2/5 | no | (comparison only) |
| b3_touch short, 5m bars | 3464 | 980 | 47.4% ±0.9 | 40.1% | +7.3 (+7.7) | 47.1% ±1.1 | 40.5% | +6.6 (+8.8) | -0.018 ±0.009 | -0.042 ±0.020 | 0/5 | no | (comparison only) |
| b3_reentry long, 1m bars | 3931 | 1232 | 50.4% ±0.8 | 38.0% | +12.5 (+13.5) | 50.6% ±0.9 | 39.5% | +11.1 (+14.9) | +0.009 ±0.008 | +0.011 ±0.014 | 3/5 | no | (comparison only) |
| b3_reentry short, 1m bars | 3734 | 1226 | 48.3% ±0.8 | 36.4% | +11.9 (+12.2) | 47.7% ±0.9 | 38.5% | +9.2 (+12.0) | -0.015 ±0.008 | -0.028 ±0.014 | 0/5 | no | (comparison only) |
| b3_reentry long, 2m bars | 2269 | 1069 | 51.3% ±1.1 | 38.3% | +13.1 (+10.6) | 50.6% ±1.1 | 41.2% | +9.3 (+9.4) | -0.011 ±0.012 | -0.005 ±0.019 | 1/5 | no | (comparison only) |
| b3_reentry short, 2m bars | 2194 | 1065 | 49.5% ±1.1 | 38.4% | +11.1 (+8.7) | 47.1% ±1.2 | 40.2% | +6.8 (+6.5) | -0.010 ±0.012 | -0.040 ±0.020 | 1/5 | no | (comparison only) |
| b3_reentry long, 3m bars | 1670 | 899 | 49.5% ±1.2 | 41.7% | +7.7 (+5.3) | 50.5% ±1.4 | 43.6% | +6.9 (+6.0) | -0.019 ±0.014 | -0.013 ±0.024 | 1/5 | no | (comparison only) |
| b3_reentry short, 3m bars | 1610 | 934 | 48.9% ±1.3 | 40.2% | +8.8 (+6.1) | 47.5% ±1.4 | 41.2% | +6.2 (+5.5) | -0.015 ±0.014 | -0.035 ±0.025 | 1/5 | no | (comparison only) |
| b3_reentry long, 4m bars | 1278 | 795 | 49.5% ±1.4 | 44.8% | +4.7 (+2.9) | 49.2% ±1.5 | 46.2% | +3.0 (+2.2) | -0.023 ±0.017 | +0.006 ±0.029 | 1/5 | no | (comparison only) |
| b3_reentry short, 4m bars | 1252 | 830 | 48.0% ±1.4 | 42.1% | +5.9 (+3.5) | 48.2% ±1.5 | 43.2% | +5.0 (+4.0) | -0.018 ±0.015 | -0.022 ±0.025 | 0/5 | no | (comparison only) |
| b3_reentry long, 5m bars | 1144 | 756 | 48.0% ±1.5 | 48.4% | -0.4 (-0.3) | 52.4% ±1.5 | 48.2% | +4.3 (+3.1) | -0.041 ±0.017 | +0.015 ±0.027 | 1/5 | no | (comparison only) |
| b3_reentry short, 5m bars | 1163 | 809 | 47.8% ±1.5 | 47.9% | -0.1 (-0.0) | 48.4% ±1.5 | 46.2% | +2.2 (+1.6) | -0.005 ±0.016 | -0.014 ±0.026 | 2/5 | no | (comparison only) |
| orb15 long, 1m bars | 303 | 303 | 51.8% ±2.9 | 65.0% | -13.2 (-3.7) | 56.1% ±2.9 | 62.4% | -6.3 (-2.1) | +0.056 ±0.029 | +0.085 ±0.044 | 0/5 | no | (comparison only) |
| orb15 short, 1m bars | 280 | 280 | 51.4% ±3.0 | 67.1% | -15.7 (-4.1) | 52.5% ±3.0 | 63.2% | -10.7 (-3.7) | +0.052 ±0.034 | +0.045 ±0.044 | 0/5 | no | (comparison only) |
| orb15 long, 5m bars | 45 | 45 | 57.8% ±7.4 | 68.9% | -11.1 (-1.5) | 53.3% ±7.5 | 71.1% | -17.8 (-2.2) | -0.021 ±0.072 | +0.021 ±0.093 | 1/5 | no | (comparison only) |
| orb15 short, 5m bars | 58 | 58 | 50.0% ±6.6 | 56.9% | -6.9 (-0.8) | 46.6% ±6.6 | 56.9% | -10.3 (-1.6) | +0.001 ±0.109 | +0.052 ±0.142 | 0/5 | no | (comparison only) |
| orb30 long, 1m bars | 299 | 299 | 52.5% ±2.9 | 63.9% | -11.4 (-3.4) | 54.8% ±2.9 | 64.9% | -10.0 (-3.2) | +0.008 ±0.027 | +0.062 ±0.041 | 0/5 | no | (comparison only) |
| orb30 short, 1m bars | 293 | 293 | 50.9% ±2.9 | 60.4% | -9.6 (-2.6) | 50.2% ±2.9 | 60.8% | -10.6 (-3.8) | +0.045 ±0.028 | +0.051 ±0.035 | 0/5 | no | (comparison only) |
| orb30 long, 5m bars | 52 | 52 | 46.2% ±7.0 | 69.2% | -23.1 (-2.5) | 46.2% ±7.0 | 69.2% | -23.1 (-3.0) | -0.078 ±0.057 | +0.014 ±0.073 | 0/5 | no | (comparison only) |
| orb30 short, 5m bars | 71 | 71 | 47.9% ±6.0 | 60.6% | -12.7 (-1.8) | 46.5% ±6.0 | 67.6% | -21.1 (-3.7) | -0.082 ±0.062 | -0.047 ±0.084 | 0/5 | no | (comparison only) |
| gap0.5_cont long | 455 | 455 | 49.2% ±2.3 | 51.9% | -2.6 (-0.9) | 53.4% ±2.3 | 51.9% | +1.5 (+0.7) | +0.007 ±0.040 | +0.050 ±0.065 | 1/5 | no | (comparison only) |
| gap0.5_cont short | 346 | 346 | 52.0% ±2.7 | 53.5% | -1.4 (-0.4) | 53.8% ±2.7 | 50.9% | +2.9 (+1.1) | +0.064 ±0.046 | +0.055 ±0.071 | 2/5 | no | (comparison only) |
| gap0.5_fill long | 346 | 346 | 46.0% ±2.7 | 47.4% | -1.4 (-0.4) | 45.1% ±2.7 | 50.3% | -5.2 (-1.9) | -0.064 ±0.046 | -0.055 ±0.071 | 0/5 | no | (comparison only) |
| gap0.5_fill short | 455 | 455 | 49.9% ±2.3 | 47.7% | +2.2 (+0.7) | 46.6% ±2.3 | 48.6% | -2.0 (-0.8) | -0.007 ±0.040 | -0.050 ±0.065 | 1/5 | no | (comparison only) |
| gap1_cont long | 287 | 287 | 52.3% ±3.0 | 54.4% | -2.1 (-0.6) | 56.4% ±2.9 | 53.7% | +2.8 (+0.9) | +0.057 ±0.054 | +0.162 ±0.091 | 1/5 | no | (comparison only) |
| gap1_cont short | 230 | 230 | 53.9% ±3.3 | 52.2% | +1.7 (+0.4) | 53.0% ±3.3 | 45.2% | +7.8 (+2.4) | +0.097 ±0.062 | +0.067 ±0.096 | 1/5 | no | (comparison only) |
| gap1_fill long | 230 | 230 | 43.9% ±3.3 | 46.5% | -2.6 (-0.6) | 46.1% ±3.3 | 50.9% | -4.8 (-1.6) | -0.097 ±0.062 | -0.067 ±0.096 | 0/5 | no | (comparison only) |
| gap1_fill short | 287 | 287 | 47.0% ±3.0 | 47.7% | -0.7 (-0.2) | 43.6% ±2.9 | 48.1% | -4.5 (-1.5) | -0.057 ±0.054 | -0.162 ±0.091 | 0/5 | no | (comparison only) |
| first_half_hour long | 448 | 448 | 52.0% ±2.4 | 64.7% | -12.7 (-4.4) | 54.9% ±2.4 | 69.2% | -14.3 (-6.2) | +0.032 ±0.027 | +0.064 ±0.040 | 0/5 | no | (comparison only) |
| first_half_hour short | 422 | 422 | 52.8% ±2.4 | 68.0% | -15.2 (-4.9) | 51.7% ±2.4 | 65.9% | -14.2 (-5.6) | +0.034 ±0.031 | +0.012 ±0.049 | 0/5 | no | (comparison only) |

Gap and first-half-hour rules at their extra horizons (control over the same number of minutes):

| Rule | Count | +5m: our way (ctrl), avg % | to 10:00: our way (ctrl), avg % | to 10:30: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|---|---|
| gap0.5_cont long | 455 | 46.4% (48.8%, z -0.8), -0.015 ±0.033 | 53.6% (49.7%, z +1.6), +0.042 ±0.060 | 50.3% (51.4%, z -0.5), +0.023 ±0.073 | 50.3% (52.3%, z -0.9), +0.054 ±0.076 | 50.3% (50.8%, z -0.3), +0.057 ±0.096 |
| gap0.5_cont short | 346 | 48.3% (53.8%, z -1.5), +0.001 ±0.035 | 50.9% (54.6%, z -1.4), +0.003 ±0.064 | 50.6% (49.7%, z +0.4), -0.064 ±0.086 | 51.4% (49.1%, z +1.0), -0.040 ±0.091 | 54.0% (54.9%, z -0.4), -0.012 ±0.109 |
| gap0.5_fill long | 346 | 50.3% (46.8%, z +1.0), -0.001 ±0.035 | 48.3% (49.1%, z -0.3), -0.003 ±0.064 | 49.1% (52.6%, z -1.3), +0.064 ±0.086 | 48.3% (52.3%, z -1.8), +0.040 ±0.091 | 46.0% (46.0%, z +0.0), +0.012 ±0.109 |
| gap0.5_fill short | 455 | 53.2% (46.8%, z +2.1), +0.015 ±0.033 | 46.2% (49.9%, z -1.4), -0.042 ±0.060 | 49.7% (49.9%, z -0.1), -0.023 ±0.073 | 49.7% (49.5%, z +0.1), -0.054 ±0.076 | 49.7% (49.5%, z +0.1), -0.057 ±0.096 |
| gap1_cont long | 287 | 49.1% (50.2%, z -0.3), +0.035 ±0.044 | 56.8% (54.0%, z +0.9), +0.144 ±0.082 | 50.5% (51.9%, z -0.6), +0.089 ±0.100 | 50.9% (50.9%, z +0.0), +0.131 ±0.103 | 51.6% (49.1%, z +1.1), +0.143 ±0.131 |
| gap1_cont short | 230 | 50.4% (51.7%, z -0.3), +0.004 ±0.047 | 50.9% (48.3%, z +0.8), +0.022 ±0.088 | 48.7% (45.2%, z +1.1), -0.119 ±0.116 | 47.8% (46.5%, z +0.5), -0.093 ±0.124 | 53.9% (50.0%, z +1.4), -0.053 ±0.143 |
| gap1_fill long | 230 | 48.3% (43.5%, z +1.0), -0.004 ±0.047 | 47.8% (49.1%, z -0.4), -0.022 ±0.088 | 50.9% (53.0%, z -0.7), +0.119 ±0.116 | 51.7% (53.0%, z -0.5), +0.093 ±0.124 | 46.1% (48.3%, z -0.9), +0.053 ±0.143 |
| gap1_fill short | 287 | 50.9% (46.0%, z +1.2), -0.035 ±0.044 | 42.9% (46.3%, z -1.0), -0.144 ±0.082 | 49.5% (50.2%, z -0.3), -0.089 ±0.100 | 49.1% (49.1%, z +0.0), -0.131 ±0.103 | 48.4% (50.2%, z -0.7), -0.143 ±0.131 |

| Rule | Count | +5m: our way (ctrl), avg % | +60m (to 11:00): our way (ctrl), avg % | to 12:00: our way (ctrl), avg % |
|---|---|---|---|---|
| first_half_hour long | 448 | 51.6% (64.3%, z -4.0), +0.042 ±0.020 | 54.7% (66.1%, z -6.1), +0.103 ±0.054 | 53.8% (62.3%, z -5.3), +0.143 ±0.068 |
| first_half_hour short | 422 | 52.1% (63.0%, z -3.4), +0.056 ±0.024 | 50.5% (59.5%, z -4.2), +0.053 ±0.069 | 50.7% (60.4%, z -5.2), +0.048 ±0.081 |

## Year by year, all9

Each cell: signals, share gap vs the control at 10 / 30 minutes (points), average move at 30 minutes (%); ✓ = the year holds.

| Rule | 2019: n, gap 10m / 30m, avg 30m | 2020: n, gap 10m / 30m, avg 30m | 2021: n, gap 10m / 30m, avg 30m | 2022: n, gap 10m / 30m, avg 30m | 2023: n, gap 10m / 30m, avg 30m | Held |
|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 448, -11.4 / -11.8, +0.022 | 411, -8.5 / -9.2, -0.009 | 400, -8.5 / -14.5, -0.007 | 389, -16.2 / -10.0, -0.064 | 472, -15.5 / -13.1, +0.047 | 0/5 |
| squeeze short, 1m bars | 411, -10.9 / -11.4, -0.018 | 403, -7.4 / -8.7, +0.072 | 398, -15.6 / -12.6, +0.005 | 355, -15.2 / -8.7, +0.075 | 378, -14.0 / -11.1, +0.002 | 0/5 |
| squeeze long, 2m bars | 196, -3.1 / -14.3, +0.025 | 161, -13.7 / -8.7, +0.100 | 173, -12.7 / -11.0, +0.092 | 120, -20.0 / -18.3, -0.054 | 148, -14.9 / -18.2, +0.023 | 0/5 |
| squeeze short, 2m bars | 155, -20.0 / -14.8, +0.013 | 147, -14.3 / -17.7, +0.107 | 148, -23.6 / -16.2, -0.016 | 123, -8.1 / -11.4, +0.097 | 117, -17.9 / -29.9, -0.012 | 0/5 |
| squeeze long, 3m bars | 126, -13.5 / -10.3, +0.019 | 107, +2.8 / -2.8, +0.068 | 122, -10.7 / -13.9, +0.130 | 88, -14.8 / -8.0, +0.216 | 126, +11.9 / -7.1, +0.065 | 0/5 |
| squeeze short, 3m bars | 113, -10.6 / -11.5, +0.038 | 80, -6.2 / -11.2, +0.053 | 95, +0.0 / -5.3, +0.040 | 99, -3.0 / -6.1, -0.038 | 112, -14.3 / -17.0, -0.152 | 0/5 |
| squeeze long, 4m bars | 111, +8.1 / +2.7, +0.011 ✓ | 109, -0.9 / +2.8, +0.210 | 101, -10.9 / -14.9, +0.144 | 96, +1.0 / +5.2, +0.162 ✓ | 131, -4.6 / -6.1, -0.045 | 2/5 |
| squeeze short, 4m bars | 96, -2.1 / -10.4, -0.048 | 67, -3.0 / -4.5, +0.083 | 86, -5.8 / -19.8, -0.082 | 74, +5.4 / +9.5, +0.121 ✓ | 91, -3.3 / -8.8, -0.061 | 1/5 |
| squeeze long, 5m bars | 159, +3.8 / +3.8, +0.008 ✓ | 135, +8.1 / +1.5, +0.210 ✓ | 154, -7.1 / -8.4, -0.062 | 117, +2.6 / -2.6, +0.041 | 149, -8.1 / +3.4, -0.026 | 2/5 |
| squeeze short, 5m bars | 113, -7.1 / -1.8, -0.008 | 92, +2.2 / -3.3, +0.134 | 118, -11.9 / -8.5, -0.035 | 131, -3.1 / -0.8, +0.024 | 156, +7.7 / +0.6, -0.032 | 0/5 |
| pullback long, 1m bars | 739, -8.7 / -7.7, +0.022 | 609, -8.2 / -10.0, +0.005 | 560, -7.5 / -10.4, +0.015 | 496, -11.9 / -12.7, +0.037 | 561, -7.1 / -6.8, +0.035 | 0/5 |
| pullback short, 1m bars | 568, -9.0 / -7.4, +0.007 | 422, -6.2 / -10.2, -0.034 | 560, -8.2 / -9.1, -0.009 | 433, -12.9 / -11.3, -0.022 | 462, -11.9 / -10.2, -0.018 | 0/5 |
| pullback long, 2m bars | 259, -6.2 / -13.5, +0.028 | 179, -13.4 / -18.4, -0.014 | 194, -8.2 / -16.0, +0.004 | 153, -15.0 / -11.1, +0.009 | 169, -5.3 / -9.5, -0.027 | 0/5 |
| pullback short, 2m bars | 193, -17.1 / -15.0, +0.015 | 142, -16.9 / -13.4, -0.057 | 179, -14.5 / -7.3, +0.007 | 117, -9.4 / -12.8, -0.019 | 148, -6.1 / -12.2, +0.005 | 0/5 |
| pullback long, 3m bars | 139, -7.9 / -16.5, +0.008 | 100, -20.0 / -22.0, -0.037 | 114, -7.0 / -10.5, +0.171 | 106, +0.9 / -12.3, +0.062 | 93, -12.9 / -6.5, +0.023 | 0/5 |
| pullback short, 3m bars | 107, -11.2 / -13.1, +0.005 | 91, -19.8 / -12.1, -0.139 | 103, -9.7 / -9.7, -0.015 | 70, -1.4 / +2.9, +0.040 | 93, -8.6 / -28.0, -0.039 | 0/5 |
| pullback long, 4m bars | 90, +1.1 / -1.1, -0.047 | 79, +1.3 / -11.4, +0.050 | 75, +0.0 / -9.3, +0.096 | 73, -20.5 / -9.6, -0.210 | 74, -10.8 / -10.8, -0.071 | 0/5 |
| pullback short, 4m bars | 83, -12.0 / -10.8, +0.056 | 67, -10.4 / +1.5, -0.080 | 72, -8.3 / -5.6, +0.132 | 63, -6.3 / +0.0, +0.132 | 81, -9.9 / -22.2, -0.021 | 0/5 |
| pullback long, 5m bars | 108, +4.6 / +0.9, -0.126 | 82, -6.1 / -15.9, -0.067 | 103, -10.7 / -4.9, -0.081 | 88, -12.5 / -3.4, +0.003 | 108, -5.6 / +3.7, +0.023 | 0/5 |
| pullback short, 5m bars | 92, -19.6 / -25.0, +0.013 | 99, -7.1 / -8.1, -0.155 | 109, -7.3 / -6.4, +0.093 | 99, -4.0 / +1.0, -0.004 | 89, -11.2 / -6.7, +0.114 | 0/5 |
| e1_trend long, 1m bars | 11870, -6.9 / -5.8, +0.006 | 12026, -5.1 / -6.7, +0.018 | 11763, -6.0 / -7.1, -0.004 | 11464, -6.7 / -6.4, -0.003 | 11801, -6.8 / -6.6, +0.006 | 0/5 |
| e1_trend short, 1m bars | 11099, -7.7 / -7.0, -0.003 | 11115, -7.4 / -7.1, -0.015 | 11641, -6.6 / -6.9, +0.005 | 11572, -7.7 / -7.3, -0.009 | 11359, -6.7 / -6.9, -0.013 | 0/5 |
| e1_trend long, 2m bars | 6015, -8.5 / -8.4, +0.004 | 6107, -7.5 / -6.8, +0.029 | 5932, -7.8 / -7.1, -0.007 | 5699, -6.4 / -8.1, +0.003 | 5948, -7.3 / -8.9, +0.001 | 0/5 |
| e1_trend short, 2m bars | 5491, -9.1 / -10.1, -0.010 | 5535, -7.8 / -9.7, -0.011 | 5993, -7.6 / -8.6, +0.013 | 5728, -6.2 / -8.6, -0.000 | 5752, -9.7 / -9.4, -0.014 | 0/5 |
| e1_trend long, 3m bars | 3911, -8.7 / -9.3, +0.001 | 4012, -9.8 / -9.2, +0.021 | 3853, -11.1 / -9.8, -0.008 | 3666, -7.1 / -9.3, +0.008 | 3897, -8.3 / -9.5, +0.001 | 0/5 |
| e1_trend short, 3m bars | 3512, -10.3 / -9.5, -0.010 | 3616, -8.5 / -8.7, -0.014 | 3846, -9.5 / -7.8, +0.009 | 3735, -9.1 / -8.6, +0.018 | 3654, -9.5 / -9.4, -0.022 | 0/5 |
| e1_trend long, 4m bars | 2780, -11.8 / -9.3, -0.005 | 2959, -9.6 / -9.4, +0.010 | 2840, -9.6 / -10.9, -0.013 | 2688, -9.2 / -9.4, -0.007 | 2881, -9.4 / -9.9, +0.002 | 0/5 |
| e1_trend short, 4m bars | 2582, -11.1 / -11.0, -0.005 | 2645, -10.4 / -11.6, -0.033 | 2797, -10.5 / -9.1, +0.018 | 2796, -10.1 / -9.2, +0.009 | 2681, -14.0 / -11.1, -0.017 | 0/5 |
| e1_trend long, 5m bars | 2580, -9.9 / -7.6, +0.016 | 2720, -9.3 / -9.3, +0.005 | 2612, -9.7 / -9.5, -0.007 | 2407, -10.3 / -9.0, -0.018 | 2639, -10.2 / -11.9, -0.004 | 0/5 |
| e1_trend short, 5m bars | 2315, -10.9 / -10.1, +0.002 | 2376, -12.3 / -10.8, -0.061 | 2462, -10.1 / -10.3, +0.010 | 2641, -9.4 / -7.2, +0.027 | 2396, -10.6 / -9.0, -0.020 | 0/5 |
| e1_reject long, 1m bars | 19502, -10.2 / -8.1, +0.009 | 19037, -9.6 / -7.7, +0.018 | 18672, -10.1 / -9.1, +0.003 | 17266, -10.9 / -8.8, -0.009 | 19504, -10.5 / -8.5, +0.010 | 0/5 |
| e1_reject short, 1m bars | 17187, -10.9 / -9.2, -0.003 | 16680, -10.3 / -9.0, -0.008 | 17974, -11.6 / -9.6, -0.004 | 17993, -9.6 / -8.5, +0.014 | 17719, -11.4 / -9.4, -0.019 | 0/5 |
| e1_reject long, 2m bars | 14079, -9.8 / -8.1, +0.008 | 13464, -9.7 / -7.3, +0.015 | 13191, -10.4 / -8.4, +0.003 | 11483, -9.4 / -8.2, -0.014 | 13392, -9.4 / -9.1, +0.013 | 0/5 |
| e1_reject short, 2m bars | 11547, -11.9 / -10.0, -0.002 | 10944, -10.4 / -9.1, -0.008 | 12384, -9.8 / -8.9, +0.003 | 11935, -8.3 / -8.2, +0.007 | 11936, -11.0 / -8.1, -0.012 | 0/5 |
| e1_reject long, 3m bars | 10837, -9.5 / -8.0, +0.006 | 10373, -8.5 / -7.1, +0.012 | 9963, -9.3 / -7.7, +0.006 | 8395, -7.2 / -8.2, -0.018 | 10195, -7.8 / -8.0, +0.012 | 0/5 |
| e1_reject short, 3m bars | 8514, -9.7 / -8.4, -0.002 | 8139, -9.6 / -6.9, -0.008 | 9516, -9.1 / -8.5, +0.005 | 8829, -7.8 / -8.3, -0.020 | 9014, -9.8 / -8.9, -0.014 | 0/5 |
| e1_reject long, 4m bars | 7843, -9.6 / -7.3, +0.003 | 7407, -8.4 / -7.3, +0.011 | 7406, -6.8 / -7.0, +0.004 | 6129, -7.9 / -5.9, -0.005 | 7562, -8.0 / -7.8, +0.008 | 0/5 |
| e1_reject short, 4m bars | 6188, -9.7 / -8.5, -0.006 | 5729, -7.7 / -7.5, -0.006 | 6902, -9.0 / -8.5, +0.004 | 6422, -7.0 / -6.5, -0.011 | 6464, -8.3 / -7.8, -0.007 | 0/5 |
| e1_reject long, 5m bars | 6160, -8.7 / -7.6, +0.007 | 5805, -8.6 / -7.9, +0.005 | 5881, -9.3 / -9.0, +0.007 | 4829, -5.5 / -7.0, -0.000 | 6040, -8.5 / -7.5, +0.012 | 0/5 |
| e1_reject short, 5m bars | 4732, -9.3 / -9.6, +0.006 | 4536, -8.8 / -9.2, -0.003 | 5528, -9.6 / -9.8, +0.006 | 5103, -7.9 / -7.4, -0.016 | 5129, -6.9 / -7.0, -0.006 | 0/5 |
| r2_rsi long, 1m bars | 2826, +9.0 / +7.8, +0.003 | 2755, +10.6 / +9.2, +0.030 ✓ | 2723, +8.6 / +8.7, +0.009 ✓ | 3272, +9.2 / +6.4, -0.073 | 2768, +12.1 / +9.6, +0.038 ✓ | 3/5 |
| r2_rsi short, 1m bars | 1946, +6.0 / +4.7, -0.028 | 1955, +8.8 / +7.3, -0.012 | 1961, +7.1 / +6.9, -0.045 | 1706, +9.4 / +7.6, -0.002 | 1955, +11.2 / +9.6, +0.017 ✓ | 1/5 |
| r2_rsi long, 2m bars | 1747, +2.3 / +1.5, -0.013 | 1507, +5.4 / +5.8, +0.067 ✓ | 1735, +4.6 / +3.5, -0.008 | 2130, +1.2 / +0.6, -0.044 | 1814, +2.0 / +2.0, +0.020 ✓ | 2/5 |
| r2_rsi short, 2m bars | 1254, -3.6 / -0.6, -0.030 | 1214, -0.3 / -0.6, -0.028 | 1243, -0.7 / -0.2, -0.060 | 970, +2.4 / -1.2, -0.035 | 1186, +3.1 / +1.1, -0.013 | 0/5 |
| r2_rsi long, 3m bars | 1528, -1.9 / -4.6, -0.006 | 1266, -0.6 / -0.5, +0.095 | 1588, -0.2 / -4.7, -0.028 | 1812, -6.3 / -4.6, -0.063 | 1533, -1.3 / -2.9, +0.001 | 0/5 |
| r2_rsi short, 3m bars | 999, -7.2 / -4.9, -0.035 | 865, -3.4 / -2.5, -0.050 | 978, -2.7 / -3.3, -0.058 | 739, -3.0 / -3.5, -0.041 | 936, -0.3 / -3.5, -0.022 | 0/5 |
| r2_rsi long, 4m bars | 1225, -3.1 / -2.1, +0.008 | 1007, -3.4 / -2.6, +0.059 | 1318, -3.2 / -4.2, -0.006 | 1522, -9.1 / -6.8, -0.023 | 1317, -7.7 / -6.8, +0.007 | 0/5 |
| r2_rsi short, 4m bars | 819, -9.4 / -7.9, -0.021 | 738, -10.0 / -7.5, -0.048 | 798, -8.9 / -6.0, -0.024 | 632, -11.1 / -7.9, -0.026 | 787, -5.6 / -3.7, -0.018 | 0/5 |
| r2_rsi long, 5m bars | 1071, -5.3 / -4.8, +0.007 | 963, -7.1 / -8.4, +0.036 | 1174, -4.1 / -9.1, -0.031 | 1323, -10.7 / -9.1, -0.049 | 1169, -10.9 / -9.1, -0.007 | 0/5 |
| r2_rsi short, 5m bars | 712, -8.3 / -7.4, -0.036 | 680, -13.8 / -12.6, -0.068 | 681, -6.6 / -10.6, -0.037 | 542, -3.1 / -8.1, +0.058 | 730, -4.7 / -8.1, +0.003 | 0/5 |
| r2_rsi_sym long, 1m bars | 1605, +11.8 / +9.7, +0.010 ✓ | 1612, +12.0 / +9.4, +0.018 | 1587, +12.7 / +9.7, +0.008 ✓ | 1863, +9.4 / +8.3, -0.066 | 1583, +14.5 / +10.4, +0.070 ✓ | 3/5 |
| r2_rsi_sym short, 1m bars | 1946, +6.1 / +5.4, -0.028 | 1955, +10.2 / +6.0, -0.012 | 1961, +7.9 / +7.5, -0.045 | 1706, +9.3 / +7.8, -0.002 | 1955, +9.8 / +10.1, +0.017 ✓ | 1/5 |
| r2_rsi_sym long, 2m bars | 927, +0.5 / +1.2, -0.008 | 814, +8.2 / +4.1, +0.100 ✓ | 989, +4.9 / +1.3, -0.009 | 1147, +1.1 / -0.9, -0.024 | 969, +4.0 / +2.8, +0.008 ✓ | 2/5 |
| r2_rsi_sym short, 2m bars | 1254, +1.5 / +0.0, -0.030 | 1214, +3.9 / +1.9, -0.028 | 1243, +0.0 / -0.2, -0.060 | 970, +3.9 / -1.3, -0.035 | 1186, +2.8 / +2.9, -0.013 | 0/5 |
| r2_rsi_sym long, 3m bars | 763, -2.8 / -2.5, -0.007 | 608, +0.7 / +0.0, +0.105 | 836, +1.4 / +0.5, -0.018 | 896, -3.7 / -1.5, -0.022 | 757, -2.9 / -4.6, +0.001 | 0/5 |
| r2_rsi_sym short, 3m bars | 999, -8.8 / -6.6, -0.035 | 865, -4.0 / -1.6, -0.050 | 978, -1.4 / -6.1, -0.058 | 739, -0.7 / -4.2, -0.041 | 936, -1.8 / -1.5, -0.022 | 0/5 |
| r2_rsi_sym long, 4m bars | 593, -4.9 / -3.5, +0.007 | 483, +5.6 / -2.3, +0.108 | 645, +0.9 / -3.1, +0.038 | 751, -8.5 / -6.0, -0.025 | 669, -7.0 / -9.1, +0.018 | 0/5 |
| r2_rsi_sym short, 4m bars | 819, -7.2 / -8.4, -0.021 | 738, -7.6 / -7.9, -0.048 | 798, -5.6 / -7.6, -0.024 | 632, -9.0 / -7.9, -0.026 | 787, -8.8 / -5.8, -0.018 | 0/5 |
| r2_rsi_sym long, 5m bars | 541, -3.3 / -3.3, -0.013 | 458, -4.8 / -5.7, +0.011 | 596, -3.4 / -7.2, -0.004 | 657, -8.4 / -9.4, -0.033 | 601, -5.3 / -7.8, +0.011 | 0/5 |
| r2_rsi_sym short, 5m bars | 712, -12.5 / -7.6, -0.036 | 680, -13.7 / -12.4, -0.068 | 681, -11.2 / -11.7, -0.037 | 542, -9.6 / -9.6, +0.058 | 730, -7.4 / -8.2, +0.003 | 0/5 |
| b3_touch long, 1m bars | 18657, +11.1 / +9.3, +0.006 ✓ | 17059, +11.1 / +9.8, +0.013 ✓ | 18606, +11.5 / +10.3, +0.011 ✓ | 16723, +10.1 / +9.0, -0.025 | 17688, +10.5 / +9.5, +0.021 ✓ | 4/5 |
| b3_touch short, 1m bars | 19875, +9.5 / +8.3, -0.010 | 17594, +9.3 / +8.0, -0.021 | 18766, +9.7 / +9.1, -0.002 | 16310, +10.8 / +9.2, +0.007 ✓ | 18960, +9.9 / +9.1, -0.001 | 1/5 |
| b3_touch long, 2m bars | 12911, +11.7 / +10.7, -0.001 | 11695, +12.2 / +11.3, +0.020 ✓ | 13152, +12.6 / +11.1, +0.007 ✓ | 11206, +11.8 / +9.8, -0.041 | 12005, +13.2 / +10.7, +0.026 ✓ | 3/5 |
| b3_touch short, 2m bars | 14050, +9.7 / +8.8, -0.010 | 11943, +11.9 / +9.1, -0.026 | 12986, +11.1 / +9.7, -0.003 | 11037, +12.4 / +11.2, +0.003 ✓ | 13029, +10.5 / +9.8, -0.003 | 1/5 |
| b3_touch long, 3m bars | 10149, +11.8 / +9.0, -0.007 | 9216, +11.9 / +10.3, +0.038 ✓ | 10602, +11.7 / +10.4, +0.003 ✓ | 9269, +10.2 / +7.4, -0.050 | 9727, +11.4 / +10.3, +0.031 ✓ | 3/5 |
| b3_touch short, 3m bars | 11620, +9.4 / +7.4, -0.011 | 9784, +9.8 / +8.7, -0.029 | 10608, +10.0 / +8.5, -0.015 | 8929, +11.3 / +9.3, +0.003 ✓ | 10611, +9.5 / +8.3, -0.008 | 1/5 |
| b3_touch long, 4m bars | 7165, +9.7 / +8.8, -0.009 | 6492, +10.5 / +8.8, +0.055 ✓ | 7588, +11.3 / +9.1, -0.001 | 6775, +8.4 / +6.4, -0.037 | 6912, +10.2 / +8.5, +0.029 ✓ | 2/5 |
| b3_touch short, 4m bars | 8236, +9.1 / +6.8, -0.003 | 7013, +9.2 / +7.4, -0.032 | 7594, +8.9 / +8.1, -0.021 | 6385, +9.4 / +8.3, -0.006 | 7650, +8.8 / +7.7, -0.003 | 0/5 |
| b3_touch long, 5m bars | 5896, +8.8 / +7.1, -0.012 | 5356, +9.3 / +8.1, +0.068 ✓ | 6294, +10.2 / +9.2, +0.008 ✓ | 5842, +8.2 / +5.5, -0.042 | 5785, +8.5 / +8.0, +0.023 ✓ | 3/5 |
| b3_touch short, 5m bars | 6870, +7.9 / +6.6, -0.012 | 6055, +9.9 / +7.4, -0.026 | 6610, +6.5 / +6.1, -0.030 | 5484, +8.0 / +6.5, -0.014 | 6580, +7.1 / +7.6, -0.001 | 0/5 |
| b3_reentry long, 1m bars | 6788, +11.8 / +10.0, +0.003 ✓ | 7047, +12.9 / +11.2, +0.022 ✓ | 6885, +14.5 / +12.4, +0.016 ✓ | 6946, +12.3 / +10.3, -0.033 | 6518, +11.5 / +11.8, +0.025 ✓ | 4/5 |
| b3_reentry short, 1m bars | 6743, +10.2 / +8.0, -0.017 | 6494, +10.9 / +9.4, -0.028 | 6339, +11.2 / +10.5, -0.001 | 6851, +11.9 / +9.6, +0.005 ✓ | 6959, +12.4 / +10.2, +0.006 ✓ | 2/5 |
| b3_reentry long, 2m bars | 3834, +10.8 / +10.0, -0.004 | 4018, +11.7 / +11.0, +0.035 ✓ | 3933, +12.3 / +10.8, +0.004 ✓ | 4103, +9.6 / +6.9, -0.065 | 3767, +12.5 / +11.2, +0.033 ✓ | 3/5 |
| b3_reentry short, 2m bars | 4072, +10.2 / +7.3, -0.010 | 3860, +10.3 / +8.2, -0.053 | 3822, +8.8 / +9.1, -0.015 | 3901, +11.1 / +8.9, -0.002 | 4040, +9.8 / +9.6, -0.000 | 0/5 |
| b3_reentry long, 3m bars | 2781, +7.9 / +6.7, -0.003 | 2825, +7.3 / +6.8, +0.052 ✓ | 2925, +7.0 / +5.3, -0.003 | 3007, +6.4 / +5.1, -0.055 | 2777, +7.6 / +6.9, +0.038 ✓ | 2/5 |
| b3_reentry short, 3m bars | 3038, +5.7 / +4.6, -0.009 | 2872, +8.5 / +7.3, -0.023 | 2896, +7.9 / +6.5, -0.021 | 2784, +9.3 / +5.9, -0.006 | 3061, +5.8 / +5.4, -0.017 | 0/5 |
| b3_reentry long, 4m bars | 2119, +8.0 / +3.8, -0.002 | 2103, +5.6 / +6.9, +0.077 ✓ | 2278, +4.7 / +3.8, -0.008 | 2372, +4.9 / +3.0, -0.052 | 2125, +6.3 / +5.9, +0.042 ✓ | 2/5 |
| b3_reentry short, 4m bars | 2376, +5.3 / +4.8, +0.010 | 2240, +5.0 / +3.3, -0.029 | 2272, +5.1 / +2.9, -0.042 | 2145, +6.9 / +3.6, +0.011 | 2403, +6.5 / +2.9, +0.006 ✓ | 1/5 |
| b3_reentry long, 5m bars | 1892, +3.7 / +3.3, -0.003 | 1927, +3.5 / +5.1, +0.075 | 2096, +1.8 / +1.7, -0.010 | 2104, +4.1 / +2.0, -0.027 | 1867, +3.9 / +4.4, +0.029 ✓ | 1/5 |
| b3_reentry short, 5m bars | 2103, +2.5 / +1.8, -0.003 | 2093, -0.2 / +3.8, -0.053 | 2119, +0.1 / +0.6, -0.041 | 1884, +7.1 / +4.1, +0.028 ✓ | 2196, +4.1 / +2.7, +0.017 ✓ | 2/5 |
| orb15 long, 1m bars | 514, -15.2 / -11.5, +0.048 | 395, -13.9 / -15.9, +0.125 | 437, -10.1 / -6.2, +0.032 | 361, -18.0 / -12.5, -0.035 | 470, -10.0 / -8.5, -0.001 | 0/5 |
| orb15 short, 1m bars | 423, -20.8 / -14.9, +0.004 | 353, -19.0 / -22.1, -0.099 | 398, -21.4 / -14.6, +0.026 | 400, -16.2 / -11.0, +0.045 | 408, -18.1 / -14.5, -0.008 | 0/5 |
| orb15 long, 5m bars | 98, -8.2 / -6.1, +0.130 | 61, -27.9 / -23.0, +0.041 | 54, -18.5 / -22.2, -0.045 | 50, -4.0 / -12.0, -0.089 | 71, -28.2 / -15.5, +0.007 | 0/5 |
| orb15 short, 5m bars | 95, -15.8 / -14.7, +0.027 | 81, -17.3 / -14.8, -0.089 | 80, -11.2 / -8.8, +0.045 | 45, -15.6 / -4.4, +0.098 | 71, -9.9 / -18.3, +0.010 | 0/5 |
| orb30 long, 1m bars | 536, -8.2 / -11.0, +0.019 | 442, -8.8 / -11.3, +0.033 | 444, -15.3 / -5.6, +0.054 | 359, -13.9 / -8.4, -0.031 | 506, -14.6 / -9.7, +0.009 | 0/5 |
| orb30 short, 1m bars | 463, -11.9 / -15.1, -0.031 | 415, -16.6 / -15.2, +0.009 | 452, -16.8 / -17.3, -0.007 | 454, -13.0 / -8.1, +0.062 | 448, -12.5 / -15.0, +0.048 | 0/5 |
| orb30 long, 5m bars | 114, -5.3 / -3.5, +0.036 | 89, -12.4 / -22.5, -0.116 | 68, -13.2 / -5.9, +0.030 | 51, -11.8 / -11.8, -0.155 | 96, -11.5 / -11.5, -0.005 | 0/5 |
| orb30 short, 5m bars | 116, -6.9 / -13.8, -0.030 | 91, -26.4 / -18.7, +0.033 | 98, -5.1 / -22.4, +0.005 | 72, -29.2 / -23.6, +0.047 | 91, -18.7 / -15.4, +0.020 | 0/5 |
| gap0.5_cont long | 611, +0.2 / +7.7, +0.105 ✓ | 872, +0.6 / +0.9, +0.034 | 597, -2.3 / +0.7, +0.030 | 636, -7.2 / +2.0, +0.096 | 610, -2.6 / -3.1, -0.011 | 1/5 |
| gap0.5_cont short | 445, +0.7 / +10.6, +0.110 ✓ | 526, +8.2 / +5.7, -0.045 | 414, -1.0 / +0.7, -0.038 | 842, -3.1 / +2.3, +0.161 | 579, +2.4 / +6.7, -0.049 | 1/5 |
| gap0.5_fill long | 445, +0.9 / -8.8, -0.110 | 526, -8.9 / -8.7, +0.045 | 414, +2.2 / +0.0, +0.038 | 842, +3.3 / -5.6, -0.161 | 579, -2.8 / -4.3, +0.049 | 0/5 |
| gap0.5_fill short | 611, +1.3 / -5.2, -0.105 | 872, +1.5 / +2.2, -0.034 | 597, +4.4 / +3.2, -0.030 | 636, +6.3 / -4.2, -0.096 | 610, +3.9 / +1.8, +0.011 ✓ | 1/5 |
| gap1_cont long | 240, +1.7 / +9.6, +0.147 ✓ | 514, -6.8 / -3.1, +0.045 | 263, -3.8 / -4.9, +0.063 | 396, -3.8 / +2.8, +0.154 | 304, -2.3 / +0.0, +0.066 | 1/5 |
| gap1_cont short | 214, -0.9 / +8.4, +0.147 | 352, +2.6 / +4.8, -0.099 | 237, -3.4 / +6.3, -0.105 | 517, -4.1 / +2.1, +0.177 | 264, -0.4 / +9.1, -0.057 | 0/5 |
| gap1_fill long | 214, -6.1 / -7.0, -0.147 | 352, -8.5 / -4.8, +0.099 | 237, +2.1 / +1.3, +0.105 ✓ | 517, +5.4 / -1.5, -0.177 | 264, +0.0 / -4.9, +0.057 | 1/5 |
| gap1_fill short | 240, -4.6 / -12.9, -0.147 | 514, +3.5 / +1.2, -0.045 | 263, +3.8 / +3.4, -0.063 | 396, +5.1 / -2.0, -0.154 | 304, +6.2 / +1.3, -0.066 | 0/5 |
| first_half_hour long | 688, -15.1 / -13.2, +0.022 | 806, -16.0 / -20.1, +0.045 | 699, -15.0 / -12.2, +0.043 | 826, -18.2 / -13.9, +0.040 | 789, -14.6 / -13.2, +0.003 | 0/5 |
| first_half_hour short | 591, -16.1 / -17.8, -0.029 | 701, -15.0 / -13.7, -0.084 | 645, -12.2 / -15.5, +0.025 | 801, -12.9 / -11.1, +0.054 | 617, -17.3 / -15.7, +0.014 | 0/5 |

## Year by year, spy

Each cell: signals, share gap vs the control at 10 / 30 minutes (points), average move at 30 minutes (%); ✓ = the year holds.

| Rule | 2019: n, gap 10m / 30m, avg 30m | 2020: n, gap 10m / 30m, avg 30m | 2021: n, gap 10m / 30m, avg 30m | 2022: n, gap 10m / 30m, avg 30m | 2023: n, gap 10m / 30m, avg 30m | Held |
|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 43, -7.0 / -16.3, +0.013 | 36, -2.8 / +0.0, +0.005 | 40, -12.5 / -25.0, -0.002 | 47, -17.0 / -8.5, -0.015 | 54, -22.2 / -9.3, +0.024 | 0/5 |
| squeeze short, 1m bars | 33, +0.0 / -9.1, +0.004 | 41, -14.6 / -12.2, +0.018 | 41, -9.8 / -31.7, -0.019 | 38, -7.9 / -2.6, -0.040 | 41, -2.4 / -17.1, +0.016 | 0/5 |
| squeeze long, 2m bars | 21, -14.3 / -28.6, -0.002 | 14, -7.1 / +7.1, -0.004 | 15, -13.3 / -26.7, -0.014 | 14, -35.7 / -57.1, -0.070 | 17, -29.4 / -11.8, -0.080 | 0/5 |
| squeeze short, 2m bars | 16, -18.8 / -18.8, -0.033 | 17, -11.8 / -23.5, -0.098 | 7, +0.0 / -14.3, +0.045 | 16, -37.5 / -31.2, -0.070 | 17, -5.9 / -23.5, +0.019 | 0/5 |
| squeeze long, 3m bars | 15, +0.0 / -6.7, -0.013 | 11, -9.1 / +9.1, -0.018 | 10, -10.0 / -20.0, +0.135 | 8, -37.5 / +0.0, -0.105 | 7, +0.0 / -14.3, -0.017 | 0/5 |
| squeeze short, 3m bars | 7, +0.0 / -28.6, -0.014 | 9, +0.0 / -11.1, +0.220 | 4, -25.0 / +0.0, -0.009 | 13, -7.7 / -7.7, +0.030 | 12, -41.7 / -16.7, +0.089 | 0/5 |
| squeeze long, 4m bars | 11, +27.3 / -9.1, +0.038 | 4, -50.0 / -25.0, -0.070 | 6, -33.3 / -33.3, +0.022 | 7, -28.6 / +0.0, -0.023 | 9, -11.1 / +11.1, -0.024 | 0/5 |
| squeeze short, 4m bars | 9, +22.2 / -22.2, -0.010 | 5, -20.0 / +20.0, +0.179 | 3, -33.3 / -33.3, -0.111 | 7, +0.0 / +0.0, +0.095 | 6, +0.0 / +0.0, +0.037 | 0/5 |
| squeeze long, 5m bars | 8, -37.5 / +12.5, +0.050 | 8, -25.0 / -12.5, -0.264 | 7, +0.0 / -28.6, +0.032 | 10, +10.0 / -10.0, +0.069 | 5, +20.0 / +0.0, -0.104 | 0/5 |
| squeeze short, 5m bars | 7, +0.0 / -14.3, -0.031 | 7, -28.6 / +14.3, +0.089 | 4, -25.0 / -25.0, -0.096 | 10, +20.0 / +20.0, +0.064 | 15, +20.0 / +13.3, +0.059 ✓ | 1/5 |
| pullback long, 1m bars | 73, +4.1 / -2.7, +0.010 | 74, -9.5 / -4.1, -0.015 | 73, +0.0 / -5.5, -0.028 | 53, -17.0 / -13.2, +0.066 | 67, -9.0 / -1.5, +0.000 | 0/5 |
| pullback short, 1m bars | 54, -9.3 / -16.7, +0.019 | 54, +11.1 / -14.8, +0.052 | 61, -3.3 / -13.1, -0.036 | 63, -11.1 / -15.9, -0.037 | 65, -18.5 / -15.4, -0.011 | 0/5 |
| pullback long, 2m bars | 29, -27.6 / -13.8, +0.040 | 26, -19.2 / -26.9, +0.039 | 27, +3.7 / +3.7, +0.048 ✓ | 19, +10.5 / +10.5, +0.078 ✓ | 22, -18.2 / -4.5, -0.006 | 2/5 |
| pullback short, 2m bars | 22, -4.5 / -4.5, -0.008 | 19, -31.6 / -10.5, -0.059 | 22, +13.6 / -9.1, -0.034 | 22, -40.9 / -22.7, -0.003 | 26, -23.1 / -19.2, -0.042 | 0/5 |
| pullback long, 3m bars | 15, +0.0 / -13.3, -0.034 | 11, -27.3 / -27.3, +0.014 | 10, -20.0 / -10.0, +0.005 | 10, +0.0 / -20.0, +0.048 | 10, -10.0 / +0.0, -0.007 | 0/5 |
| pullback short, 3m bars | 7, +14.3 / -14.3, -0.037 | 6, +0.0 / -16.7, -0.010 | 9, -11.1 / -11.1, +0.082 | 9, -11.1 / +11.1, -0.116 | 11, -36.4 / -45.5, -0.042 | 0/5 |
| pullback long, 4m bars | 13, +0.0 / -7.7, -0.031 | 9, +44.4 / +0.0, +0.007 | 3, -33.3 / +33.3, +0.005 | 1, +0.0 / +0.0, -0.255 | 5, -20.0 / +0.0, +0.066 | 0/5 |
| pullback short, 4m bars | 7, +0.0 / -14.3, -0.036 | 4, -25.0 / +0.0, +0.297 | 4, -25.0 / -50.0, +0.045 | 1, +0.0 / +0.0, -1.372 | 2, -50.0 / +0.0, -0.003 | 0/5 |
| pullback long, 5m bars | 6, -16.7 / -33.3, -0.038 | 2, -50.0 / -50.0, -0.048 | 5, -40.0 / -40.0, -0.008 | 2, +0.0 / +50.0, +0.068 | 3, -33.3 / +33.3, +0.082 | 0/5 |
| pullback short, 5m bars | 8, -25.0 / -37.5, -0.011 | 3, -33.3 / +0.0, -0.156 | 3, -33.3 / -33.3, +0.181 | 4, +50.0 / +0.0, +0.116 | 5, -20.0 / +0.0, -0.081 | 0/5 |
| e1_trend long, 1m bars | 1321, -7.0 / -3.6, +0.006 | 1379, -4.0 / -6.2, +0.011 | 1316, -3.9 / -6.9, +0.001 | 1295, -6.6 / -7.9, +0.000 | 1324, -7.3 / -4.7, +0.003 | 0/5 |
| e1_trend short, 1m bars | 1189, -7.9 / -6.2, -0.005 | 1176, -4.8 / -8.2, -0.015 | 1233, -7.5 / -6.9, -0.001 | 1258, -6.6 / -5.9, -0.004 | 1247, -6.4 / -6.8, -0.007 | 0/5 |
| e1_trend long, 2m bars | 688, -12.5 / -9.2, +0.002 | 664, -7.1 / -7.4, +0.013 | 666, -8.7 / -6.3, +0.005 | 628, -6.5 / -9.7, -0.001 | 665, -4.4 / -8.1, -0.001 | 0/5 |
| e1_trend short, 2m bars | 587, -9.2 / -10.4, -0.012 | 584, -9.4 / -9.6, -0.031 | 609, -11.0 / -9.2, +0.003 | 606, -11.1 / -7.3, +0.008 | 633, -11.8 / -10.9, -0.013 | 0/5 |
| e1_trend long, 3m bars | 448, -9.4 / -8.9, +0.004 | 444, -6.1 / -7.4, +0.033 | 447, -11.6 / -6.0, +0.001 | 421, -4.5 / -11.4, -0.001 | 424, -9.4 / -10.8, -0.003 | 0/5 |
| e1_trend short, 3m bars | 383, -8.4 / -11.0, +0.001 | 382, -9.7 / -7.1, -0.015 | 372, -8.6 / -7.0, +0.013 | 406, -8.6 / -9.9, +0.001 | 404, -11.9 / -10.1, -0.011 | 0/5 |
| e1_trend long, 4m bars | 317, -19.6 / -8.8, -0.006 | 320, -9.4 / -7.5, +0.034 | 319, -7.5 / -9.4, +0.002 | 305, -10.5 / -15.4, -0.011 | 326, -8.9 / -12.3, -0.007 | 0/5 |
| e1_trend short, 4m bars | 275, -8.0 / -11.6, -0.015 | 285, -14.0 / -16.8, -0.043 | 273, -10.6 / -11.4, +0.012 | 311, -10.3 / -13.2, -0.007 | 298, -14.4 / -6.7, -0.010 | 0/5 |
| e1_trend long, 5m bars | 276, -7.6 / -7.6, -0.001 | 300, -8.0 / -9.7, +0.012 | 289, -9.3 / -8.0, +0.021 | 262, -8.4 / -8.8, -0.013 | 296, -11.8 / -14.2, -0.010 | 0/5 |
| e1_trend short, 5m bars | 264, -10.2 / -9.1, -0.002 | 261, -14.2 / -11.5, -0.024 | 237, -7.2 / -12.2, +0.019 | 277, -9.0 / -6.5, +0.034 | 265, -14.0 / -6.8, -0.012 | 0/5 |
| e1_reject long, 1m bars | 2453, -9.3 / -8.4, +0.005 | 2428, -8.9 / -7.7, +0.008 | 2483, -9.6 / -9.6, +0.011 | 2184, -10.3 / -10.0, -0.006 | 2407, -11.0 / -7.6, +0.003 | 0/5 |
| e1_reject short, 1m bars | 1996, -10.4 / -9.9, -0.004 | 1848, -10.7 / -9.7, -0.003 | 2033, -11.8 / -9.5, -0.003 | 2123, -9.0 / -10.1, +0.002 | 2060, -12.6 / -8.4, -0.008 | 0/5 |
| e1_reject long, 2m bars | 1864, -12.3 / -7.5, +0.006 | 1832, -10.8 / -6.7, +0.006 | 1917, -9.9 / -9.0, +0.010 | 1498, -9.5 / -8.8, -0.012 | 1804, -10.1 / -9.1, +0.003 | 0/5 |
| e1_reject short, 2m bars | 1385, -10.2 / -8.9, -0.003 | 1218, -10.8 / -9.9, +0.004 | 1393, -12.1 / -8.7, -0.001 | 1433, -9.0 / -8.9, -0.006 | 1486, -13.0 / -9.5, -0.009 | 0/5 |
| e1_reject long, 3m bars | 1475, -9.4 / -7.3, +0.010 | 1421, -8.9 / -6.0, +0.009 | 1515, -10.6 / -7.7, +0.011 | 1121, -7.1 / -9.4, -0.007 | 1447, -9.9 / -8.8, +0.007 | 0/5 |
| e1_reject short, 3m bars | 1035, -11.7 / -9.1, -0.003 | 884, -9.3 / -7.0, -0.007 | 1077, -4.9 / -7.4, +0.004 | 1093, -10.3 / -9.1, -0.023 | 1128, -9.3 / -8.8, -0.011 | 0/5 |
| e1_reject long, 4m bars | 1060, -9.9 / -8.4, +0.012 | 1013, -9.4 / -7.3, +0.008 | 1117, -6.1 / -5.4, +0.013 | 793, -10.7 / -8.2, -0.007 | 1044, -10.0 / -9.4, +0.006 | 0/5 |
| e1_reject short, 4m bars | 749, -8.4 / -9.2, -0.009 | 639, -13.6 / -11.3, -0.009 | 782, -11.6 / -9.1, +0.005 | 781, -7.0 / -7.9, -0.020 | 794, -10.1 / -7.2, -0.008 | 0/5 |
| e1_reject long, 5m bars | 806, -10.7 / -6.3, +0.011 | 783, -11.7 / -8.2, +0.005 | 868, -10.1 / -9.9, +0.006 | 616, -7.0 / -4.4, -0.008 | 816, -7.8 / -7.4, +0.009 | 0/5 |
| e1_reject short, 5m bars | 569, -13.4 / -9.7, -0.004 | 493, -7.5 / -10.5, +0.008 | 589, -9.7 / -9.3, -0.001 | 604, -10.8 / -7.0, -0.016 | 607, -9.2 / -8.2, -0.010 | 0/5 |
| r2_rsi long, 1m bars | 366, +7.4 / +9.0, -0.006 | 364, +6.6 / +5.2, +0.012 | 339, +5.6 / +6.8, +0.021 ✓ | 379, +9.2 / +4.0, -0.061 | 326, +13.2 / +12.3, +0.001 ✓ | 2/5 |
| r2_rsi short, 1m bars | 248, +6.9 / +6.0, +0.001 | 235, +6.8 / +6.0, +0.030 ✓ | 243, +3.7 / +5.8, -0.043 | 209, -0.5 / +4.3, -0.021 | 234, +16.7 / +10.3, +0.032 ✓ | 2/5 |
| r2_rsi long, 2m bars | 238, +8.8 / +5.0, -0.000 | 196, +2.0 / +5.1, +0.012 | 212, +4.2 / +8.5, -0.005 | 255, -3.5 / -0.8, -0.054 | 210, +3.8 / -1.0, -0.013 | 0/5 |
| r2_rsi short, 2m bars | 160, -5.0 / +0.0, -0.018 | 128, +7.0 / +3.1, -0.005 | 152, -16.4 / -2.6, -0.042 | 120, -3.3 / -0.8, -0.014 | 144, +1.4 / -1.4, +0.009 | 0/5 |
| r2_rsi long, 3m bars | 203, +2.0 / -2.0, -0.004 | 164, -3.0 / +1.2, +0.027 | 198, +3.5 / -5.1, -0.014 | 198, -6.1 / -5.1, -0.057 | 174, -6.3 / -8.0, +0.014 | 0/5 |
| r2_rsi short, 3m bars | 119, -13.4 / -1.7, -0.022 | 91, -7.7 / -11.0, +0.003 | 117, -4.3 / -7.7, -0.037 | 98, -16.3 / -2.0, -0.016 | 100, -1.0 / -6.0, +0.018 | 0/5 |
| r2_rsi long, 4m bars | 159, +0.6 / +0.6, +0.012 | 128, -8.6 / -1.6, +0.021 | 167, +0.0 / -4.2, -0.013 | 152, -9.9 / -8.6, -0.050 | 148, -8.1 / -6.8, -0.014 | 0/5 |
| r2_rsi short, 4m bars | 102, +0.0 / -7.8, -0.009 | 92, -4.3 / +1.1, +0.001 | 93, -14.0 / -14.0, -0.022 | 87, -11.5 / -6.9, -0.035 | 93, +2.2 / -1.1, +0.046 | 0/5 |
| r2_rsi long, 5m bars | 140, -8.6 / -3.6, -0.037 | 123, -9.8 / -8.9, -0.030 | 147, +0.0 / -10.9, -0.042 | 133, -14.3 / -9.0, -0.033 | 132, -14.4 / -7.6, -0.010 | 0/5 |
| r2_rsi short, 5m bars | 97, -5.2 / -13.4, -0.020 | 81, -19.8 / -9.9, -0.042 | 81, -6.2 / -7.4, -0.006 | 69, -11.6 / -10.1, +0.066 | 84, +3.6 / -8.3, +0.025 | 0/5 |
| r2_rsi_sym long, 1m bars | 203, +6.4 / +8.4, -0.008 | 217, +8.8 / +9.2, +0.036 | 195, +17.4 / +9.2, +0.023 ✓ | 223, +9.0 / +10.8, -0.040 | 182, +8.8 / +12.1, +0.006 ✓ | 2/5 |
| r2_rsi_sym short, 1m bars | 248, +5.6 / +7.3, +0.001 | 235, +12.8 / +10.6, +0.030 ✓ | 243, +4.9 / +9.1, -0.043 | 209, +1.9 / +4.8, -0.021 | 234, +11.1 / +10.7, +0.032 ✓ | 2/5 |
| r2_rsi_sym long, 2m bars | 119, +5.0 / +5.9, -0.009 | 107, -0.9 / +0.9, +0.082 | 117, +7.7 / -0.9, +0.002 | 124, +10.5 / +0.0, +0.001 | 115, +12.2 / -2.6, -0.005 | 0/5 |
| r2_rsi_sym short, 2m bars | 160, -1.2 / +0.0, -0.018 | 128, +1.6 / -1.6, -0.005 | 152, -7.2 / -2.6, -0.042 | 120, +2.5 / -1.7, -0.014 | 144, +4.9 / +3.5, +0.009 ✓ | 1/5 |
| r2_rsi_sym long, 3m bars | 100, +0.0 / -1.0, -0.016 | 75, -9.3 / -5.3, -0.003 | 101, +4.0 / -2.0, -0.004 | 95, -8.4 / -10.5, -0.030 | 75, -2.7 / -10.7, -0.018 | 0/5 |
| r2_rsi_sym short, 3m bars | 119, -16.0 / -10.1, -0.022 | 91, -3.3 / -6.6, +0.003 | 117, +1.7 / -6.0, -0.037 | 98, -6.1 / -1.0, -0.016 | 100, +3.0 / +0.0, +0.018 | 0/5 |
| r2_rsi_sym long, 4m bars | 81, +0.0 / -1.2, +0.017 | 47, -2.1 / -2.1, +0.020 | 82, +8.5 / -4.9, -0.007 | 69, -13.0 / -4.3, -0.033 | 70, -2.9 / -22.9, -0.019 | 0/5 |
| r2_rsi_sym short, 4m bars | 102, -9.8 / -10.8, -0.009 | 92, -16.3 / -2.2, +0.001 | 93, -19.4 / -14.0, -0.022 | 87, -16.1 / -8.0, -0.035 | 93, -8.6 / -5.4, +0.046 | 0/5 |
| r2_rsi_sym long, 5m bars | 64, -3.1 / -7.8, -0.037 | 50, -14.0 / -10.0, +0.002 | 78, -1.3 / -10.3, -0.015 | 62, -4.8 / +1.6, -0.042 | 61, -3.3 / -6.6, +0.016 | 0/5 |
| r2_rsi_sym short, 5m bars | 97, -11.3 / -7.2, -0.020 | 81, -14.8 / -13.6, -0.042 | 81, -13.6 / -16.0, -0.006 | 69, -26.1 / -13.0, +0.066 | 84, -2.4 / -4.8, +0.025 | 0/5 |
| b3_touch long, 1m bars | 2298, +11.3 / +8.8, +0.005 ✓ | 2110, +10.1 / +10.4, +0.007 ✓ | 2228, +12.8 / +10.0, +0.006 ✓ | 2227, +9.4 / +10.2, -0.004 | 2356, +9.3 / +8.2, +0.009 ✓ | 4/5 |
| b3_touch short, 1m bars | 2593, +9.6 / +7.4, -0.008 | 2437, +9.3 / +7.7, -0.002 | 2585, +9.4 / +8.3, -0.007 | 2237, +8.3 / +7.7, +0.003 | 2635, +9.7 / +8.3, -0.002 | 0/5 |
| b3_touch long, 2m bars | 1784, +8.0 / +9.4, -0.001 | 1523, +9.3 / +10.4, +0.013 ✓ | 1785, +14.7 / +9.4, +0.011 ✓ | 1515, +13.5 / +9.8, -0.009 | 1727, +14.4 / +9.4, +0.014 ✓ | 3/5 |
| b3_touch short, 2m bars | 2113, +8.1 / +7.3, -0.006 | 1764, +12.4 / +8.6, -0.001 | 2024, +11.4 / +7.6, -0.005 | 1538, +11.4 / +11.2, -0.000 | 1964, +10.7 / +9.1, -0.000 | 0/5 |
| b3_touch long, 3m bars | 1462, +9.8 / +8.0, -0.004 | 1174, +13.9 / +7.2, +0.019 ✓ | 1477, +12.1 / +10.6, +0.008 ✓ | 1198, +11.6 / +7.1, -0.011 | 1383, +9.1 / +8.9, +0.012 ✓ | 3/5 |
| b3_touch short, 3m bars | 1761, +8.6 / +6.4, -0.007 | 1406, +9.6 / +9.0, +0.004 ✓ | 1641, +7.9 / +6.4, -0.014 | 1185, +11.0 / +7.2, -0.007 | 1603, +8.9 / +6.8, -0.001 | 1/5 |
| b3_touch long, 4m bars | 1017, +7.9 / +8.2, -0.003 | 804, +10.1 / +6.3, +0.027 ✓ | 1007, +11.1 / +8.2, +0.006 ✓ | 812, +8.1 / +6.2, -0.010 | 958, +9.0 / +5.7, +0.010 ✓ | 3/5 |
| b3_touch short, 4m bars | 1220, +6.5 / +3.9, -0.001 | 975, +7.3 / +7.6, +0.000 | 1178, +9.3 / +7.5, -0.025 | 810, +4.9 / +5.9, -0.010 | 1092, +6.7 / +6.7, -0.003 | 0/5 |
| b3_touch long, 5m bars | 773, +8.5 / +7.6, -0.013 | 648, +9.3 / +5.9, +0.039 ✓ | 808, +8.5 / +7.4, +0.002 ✓ | 670, +8.7 / +4.8, -0.010 | 783, +10.7 / +7.7, +0.002 ✓ | 3/5 |
| b3_touch short, 5m bars | 945, +6.9 / +5.4, -0.003 | 763, +6.7 / +5.1, +0.004 ✓ | 945, +9.5 / +7.8, -0.023 | 660, +8.9 / +7.3, -0.013 | 912, +6.6 / +7.7, -0.001 | 1/5 |
| b3_reentry long, 1m bars | 772, +13.9 / +10.5, +0.002 ✓ | 815, +18.5 / +11.2, +0.024 ✓ | 739, +15.2 / +14.5, +0.012 ✓ | 786, +14.8 / +9.9, +0.004 ✓ | 738, +10.0 / +12.6, +0.008 ✓ | 5/5 |
| b3_reentry short, 1m bars | 750, +8.7 / +8.5, -0.013 | 713, +13.7 / +8.6, -0.005 | 681, +10.4 / +8.2, -0.005 | 795, +12.7 / +6.4, +0.006 ✓ | 775, +7.7 / +10.5, +0.002 ✓ | 2/5 |
| b3_reentry long, 2m bars | 434, +14.5 / +12.4, -0.006 | 452, +12.6 / +13.3, +0.035 | 411, +13.4 / +13.9, +0.018 ✓ | 465, +10.5 / +5.4, -0.045 | 422, +10.9 / +11.1, +0.014 ✓ | 2/5 |
| b3_reentry short, 2m bars | 467, +9.4 / +7.1, -0.014 | 394, +8.4 / +7.1, -0.000 | 398, +12.1 / +10.6, -0.021 | 417, +10.8 / +9.8, -0.004 | 443, +11.3 / +12.0, +0.004 | 0/5 |
| b3_reentry long, 3m bars | 317, +8.2 / +9.5, -0.005 | 317, +4.1 / +4.1, +0.024 ✓ | 302, +4.6 / +3.0, +0.013 | 332, +3.6 / +6.0, -0.044 | 284, +7.4 / +7.4, +0.012 ✓ | 2/5 |
| b3_reentry short, 3m bars | 336, +3.9 / +1.2, -0.001 | 286, +9.8 / +8.7, -0.003 | 313, +2.2 / +3.8, -0.036 | 287, +5.2 / +4.9, -0.000 | 324, +2.5 / +6.2, -0.013 | 0/5 |
| b3_reentry long, 4m bars | 214, +11.2 / -0.9, -0.003 | 237, +8.0 / +5.1, +0.041 ✓ | 236, +3.8 / +1.3, +0.007 | 253, +5.9 / +6.3, -0.014 | 214, +7.0 / +5.1, +0.014 ✓ | 2/5 |
| b3_reentry short, 4m bars | 262, +6.5 / +1.9, +0.010 ✓ | 216, +9.7 / +4.6, +0.007 | 223, -2.7 / +0.4, -0.052 | 212, +12.7 / +9.0, +0.006 ✓ | 252, +4.0 / +2.4, -0.005 | 2/5 |
| b3_reentry long, 5m bars | 202, +7.4 / -0.5, -0.010 | 209, +3.8 / +4.8, +0.050 ✓ | 213, +0.5 / +5.2, +0.013 | 205, +0.5 / +6.8, -0.019 | 183, +9.8 / +6.6, +0.008 ✓ | 2/5 |
| b3_reentry short, 5m bars | 216, +13.0 / +0.5, +0.007 | 197, -0.5 / +7.6, -0.000 | 217, +6.5 / -4.6, -0.040 | 192, +8.3 / +13.5, +0.016 ✓ | 239, -3.3 / +3.3, +0.000 | 1/5 |
| orb15 long, 1m bars | 100, -25.0 / -11.0, +0.039 | 102, -12.7 / -7.8, +0.042 | 100, -8.0 / +0.0, +0.049 | 73, -19.2 / -13.7, -0.013 | 97, -14.4 / -7.2, +0.003 | 0/5 |
| orb15 short, 1m bars | 99, -10.1 / -18.2, -0.017 | 81, -22.2 / -16.0, -0.037 | 96, -14.6 / -13.5, +0.033 | 81, -21.0 / -16.0, +0.013 | 95, -23.2 / -20.0, -0.004 | 0/5 |
| orb15 long, 5m bars | 37, -5.4 / +0.0, +0.033 | 16, -18.8 / -12.5, -0.064 | 14, -14.3 / -21.4, +0.045 | 12, +0.0 / +8.3, -0.020 | 28, -32.1 / -17.9, +0.030 | 0/5 |
| orb15 short, 5m bars | 36, +2.8 / -13.9, +0.029 | 31, -32.3 / -12.9, +0.080 | 30, -13.3 / -3.3, +0.011 | 17, -11.8 / -5.9, -0.027 | 30, -10.0 / -30.0, +0.012 | 0/5 |
| orb30 long, 1m bars | 84, -14.3 / -2.4, +0.042 | 98, -6.1 / -7.1, -0.012 | 87, -18.4 / -8.0, +0.031 | 73, -13.7 / -4.1, +0.019 | 90, -17.8 / +2.2, +0.039 | 0/5 |
| orb30 short, 1m bars | 89, -10.1 / -13.5, +0.001 | 85, -35.3 / -21.2, +0.014 | 84, -15.5 / -17.9, -0.010 | 83, -13.3 / -8.4, +0.034 | 98, -21.4 / -18.4, -0.015 | 0/5 |
| orb30 long, 5m bars | 37, -8.1 / -2.7, +0.009 | 21, +19.0 / +4.8, -0.035 | 19, -10.5 / +0.0, +0.027 | 14, -7.1 / -7.1, +0.066 | 32, -3.1 / -12.5, +0.006 | 0/5 |
| orb30 short, 5m bars | 36, +5.6 / -22.2, -0.012 | 33, -21.2 / -18.2, +0.059 | 31, -9.7 / -29.0, -0.014 | 20, -20.0 / -20.0, +0.051 | 34, -26.5 / -26.5, +0.030 | 0/5 |
| gap0.5_cont long | 40, +2.5 / +5.0, +0.049 ✓ | 77, +6.5 / +1.3, -0.046 | 35, -8.6 / -5.7, +0.080 | 55, -12.7 / +3.6, +0.119 | 39, +0.0 / -17.9, -0.018 | 1/5 |
| gap0.5_cont short | 30, +0.0 / +10.0, +0.156 | 46, +2.2 / +8.7, -0.021 | 28, +3.6 / +3.6, +0.064 ✓ | 70, +12.9 / +8.6, +0.178 ✓ | 33, -6.1 / +21.2, +0.018 | 2/5 |
| gap0.5_fill long | 30, +6.7 / -6.7, -0.156 | 46, +6.5 / +0.0, +0.021 | 28, -10.7 / -7.1, -0.064 | 70, -11.4 / -17.1, -0.178 | 33, +0.0 / -9.1, -0.018 | 0/5 |
| gap0.5_fill short | 40, +10.0 / -7.5, -0.049 | 77, +6.5 / +1.3, +0.046 ✓ | 35, +20.0 / +8.6, -0.080 | 55, -1.8 / -5.5, -0.119 | 39, +0.0 / +7.7, +0.018 | 1/5 |
| gap1_cont long | 6, -33.3 / +0.0, +0.153 | 36, -8.3 / -5.6, +0.045 | 5, +0.0 / +0.0, +0.277 | 23, -13.0 / +8.7, +0.171 | 3, +66.7 / +33.3, +0.328 ✓ | 1/5 |
| gap1_cont short | 7, +42.9 / +14.3, +0.125 ✓ | 28, -14.3 / +10.7, -0.021 | 9, -11.1 / +11.1, +0.190 | 32, +3.1 / +21.9, +0.233 ✓ | 7, +0.0 / +28.6, -0.038 | 2/5 |
| gap1_fill long | 7, +0.0 / -14.3, -0.125 | 28, -3.6 / -14.3, +0.021 | 9, +0.0 / +0.0, -0.190 | 32, +9.4 / -12.5, -0.233 | 7, +28.6 / -14.3, +0.038 | 0/5 |
| gap1_fill short | 6, -16.7 / -16.7, -0.153 | 36, +11.1 / +11.1, -0.045 | 5, +0.0 / +20.0, -0.277 | 23, +13.0 / +4.3, -0.171 | 3, -33.3 / -33.3, -0.328 | 0/5 |
| first_half_hour long | 22, -27.3 / -22.7, +0.104 | 44, -18.2 / -29.5, +0.083 | 32, -21.9 / -12.5, +0.057 | 61, -24.6 / -11.5, -0.043 | 22, -45.5 / -27.3, -0.055 | 0/5 |
| first_half_hour short | 19, -15.8 / -31.6, +0.014 | 43, -39.5 / -20.9, -0.197 | 25, -20.0 / -24.0, +0.063 | 58, -12.1 / -10.3, -0.008 | 24, -8.3 / -12.5, -0.098 | 0/5 |

## Year by year, atr_pick

Each cell: signals, share gap vs the control at 10 / 30 minutes (points), average move at 30 minutes (%); ✓ = the year holds.

| Rule | 2019: n, gap 10m / 30m, avg 30m | 2020: n, gap 10m / 30m, avg 30m | 2021: n, gap 10m / 30m, avg 30m | 2022: n, gap 10m / 30m, avg 30m | 2023: n, gap 10m / 30m, avg 30m | Held |
|---|---|---|---|---|---|---|
| squeeze long, 1m bars | 65, -16.9 / -1.5, +0.004 | 72, -13.9 / -15.3, -0.114 | 63, -1.6 / -11.1, -0.005 | 41, -7.3 / -7.3, -0.029 | 50, -16.0 / -12.0, +0.039 | 0/5 |
| squeeze short, 1m bars | 56, -25.0 / -7.1, -0.030 | 65, -6.2 / -10.8, +0.193 | 56, -7.1 / -17.9, +0.056 | 48, -25.0 / -22.9, +0.100 | 52, -9.6 / -15.4, +0.085 | 0/5 |
| squeeze long, 2m bars | 18, +16.7 / -11.1, +0.134 | 31, -19.4 / -9.7, +0.307 | 20, -10.0 / -15.0, +0.141 | 9, -11.1 / -11.1, +0.349 | 18, -16.7 / -16.7, +0.026 | 0/5 |
| squeeze short, 2m bars | 23, -8.7 / -13.0, +0.098 | 20, -10.0 / -25.0, +0.345 | 18, -33.3 / -38.9, -0.048 | 17, -23.5 / -5.9, +0.279 | 17, -17.6 / -47.1, -0.266 | 0/5 |
| squeeze long, 3m bars | 16, -18.8 / -12.5, +0.059 | 20, -10.0 / -5.0, +0.248 | 12, +0.0 / -16.7, +0.258 | 11, +9.1 / +0.0, +0.237 | 15, +40.0 / +0.0, +0.136 | 0/5 |
| squeeze short, 3m bars | 15, -20.0 / -6.7, +0.196 | 17, +5.9 / +5.9, +0.230 ✓ | 10, +30.0 / +20.0, +0.599 | 17, +23.5 / +11.8, +0.005 ✓ | 19, -36.8 / -31.6, -0.548 | 2/5 |
| squeeze long, 4m bars | 15, +0.0 / +0.0, +0.126 | 20, -10.0 / -5.0, +0.093 | 9, +22.2 / -22.2, -0.113 | 17, -5.9 / -5.9, +0.024 | 22, -18.2 / +4.5, -0.233 | 0/5 |
| squeeze short, 4m bars | 13, +23.1 / -23.1, -0.169 | 14, +0.0 / +0.0, +0.511 | 12, -16.7 / -33.3, +0.122 | 12, +0.0 / +8.3, +0.309 | 15, +6.7 / +6.7, +0.006 | 0/5 |
| squeeze long, 5m bars | 22, +4.5 / +9.1, +0.125 ✓ | 19, +5.3 / +0.0, +0.226 | 16, -31.2 / -12.5, -0.111 | 15, -33.3 / +0.0, +0.265 | 21, -19.0 / +0.0, -0.321 | 1/5 |
| squeeze short, 5m bars | 11, +9.1 / -18.2, +0.162 | 15, -20.0 / -13.3, +0.858 | 20, +5.0 / +5.0, +0.168 ✓ | 17, +5.9 / -5.9, -0.019 | 30, -3.3 / +0.0, -0.150 | 1/5 |
| pullback long, 1m bars | 92, -9.8 / -2.2, +0.051 | 84, -3.6 / -13.1, -0.029 | 61, -11.5 / -13.1, +0.049 | 72, -16.7 / -6.9, +0.140 | 56, -7.1 / -7.1, +0.079 | 0/5 |
| pullback short, 1m bars | 67, -11.9 / +1.5, +0.056 | 45, +4.4 / +8.9, -0.022 | 54, -1.9 / -3.7, +0.167 | 50, -22.0 / -18.0, +0.072 | 56, -21.4 / -3.6, +0.060 | 0/5 |
| pullback long, 2m bars | 44, -18.2 / -15.9, +0.152 | 21, -14.3 / -19.0, +0.047 | 31, -16.1 / -16.1, -0.073 | 18, +0.0 / -27.8, +0.255 | 23, -4.3 / +0.0, -0.227 | 0/5 |
| pullback short, 2m bars | 26, -15.4 / -11.5, +0.109 | 17, -23.5 / -11.8, -0.151 | 22, -31.8 / -9.1, +0.168 | 15, -20.0 / -13.3, +0.104 | 28, -7.1 / +0.0, +0.110 | 0/5 |
| pullback long, 3m bars | 17, +0.0 / +0.0, -0.084 | 16, -18.8 / -31.2, -0.036 | 16, -25.0 / -18.8, -0.017 | 20, +5.0 / -20.0, +0.260 | 15, -20.0 / +0.0, +0.022 | 0/5 |
| pullback short, 3m bars | 16, +12.5 / +0.0, +0.078 | 21, -14.3 / -14.3, -0.291 | 13, -15.4 / -7.7, +0.079 | 11, -9.1 / -18.2, +0.225 | 13, -15.4 / -23.1, +0.338 | 0/5 |
| pullback long, 4m bars | 13, -15.4 / -7.7, -0.080 | 12, +0.0 / -16.7, -0.162 | 11, -18.2 / +0.0, +0.241 | 13, -7.7 / -7.7, +0.316 | 9, +0.0 / -11.1, +0.151 | 0/5 |
| pullback short, 4m bars | 15, -46.7 / +0.0, -0.017 | 13, +7.7 / +30.8, +0.081 ✓ | 17, +11.8 / +11.8, +0.533 ✓ | 15, +6.7 / +0.0, +0.993 | 12, +16.7 / -16.7, +0.026 | 2/5 |
| pullback long, 5m bars | 17, +0.0 / +5.9, -0.263 | 12, -8.3 / -33.3, -0.066 | 14, +0.0 / +7.1, -0.348 | 11, +0.0 / +0.0, +0.765 | 11, -18.2 / +0.0, +0.095 | 0/5 |
| pullback short, 5m bars | 7, -42.9 / -28.6, -0.162 | 11, -27.3 / -27.3, -0.362 | 17, -11.8 / +0.0, +0.564 | 21, -4.8 / +9.5, +0.351 | 20, -10.0 / -5.0, +0.289 | 0/5 |
| e1_trend long, 1m bars | 1289, -5.3 / -6.6, +0.037 | 1386, -6.1 / -7.5, +0.035 | 1255, -4.5 / -5.0, +0.000 | 1268, -6.6 / -5.4, +0.002 | 1270, -5.7 / -8.0, +0.017 | 0/5 |
| e1_trend short, 1m bars | 1218, -8.0 / -4.9, +0.017 | 1249, -10.2 / -7.8, +0.005 | 1275, -7.1 / -6.4, +0.025 | 1309, -7.8 / -6.7, -0.002 | 1240, -4.9 / -6.4, +0.025 | 0/5 |
| e1_trend long, 2m bars | 638, -8.2 / -11.3, +0.037 | 699, -8.3 / -9.4, -0.005 | 621, -3.7 / -5.5, -0.010 | 624, -7.7 / -9.1, -0.004 | 619, -7.1 / -8.2, +0.012 | 0/5 |
| e1_trend short, 2m bars | 593, -7.8 / -10.5, -0.020 | 614, -9.1 / -11.4, -0.005 | 633, -5.1 / -4.4, +0.042 | 637, -7.4 / -11.5, -0.022 | 618, -7.4 / -5.7, +0.028 | 0/5 |
| e1_trend long, 3m bars | 436, -7.1 / -10.3, +0.027 | 478, -12.1 / -8.6, -0.016 | 413, -11.1 / -9.2, -0.023 | 368, -12.0 / -8.7, -0.017 | 385, -4.7 / -9.6, +0.026 | 0/5 |
| e1_trend short, 3m bars | 377, -9.8 / -10.9, -0.024 | 382, -12.8 / -11.0, -0.018 | 409, -7.6 / -5.6, +0.015 | 415, -8.7 / -8.2, +0.008 | 415, -6.0 / -10.1, +0.013 | 0/5 |
| e1_trend long, 4m bars | 314, -8.6 / -8.6, +0.029 | 335, -12.5 / -12.8, -0.039 | 298, -5.0 / -12.4, -0.020 | 282, -11.7 / -7.8, -0.057 | 292, -6.5 / -9.2, +0.010 | 0/5 |
| e1_trend short, 4m bars | 276, -6.2 / -12.7, +0.000 | 291, -9.3 / -13.1, -0.057 | 299, -10.0 / -8.7, +0.008 | 292, -11.3 / -11.6, +0.039 | 300, -12.0 / -12.7, +0.015 | 0/5 |
| e1_trend long, 5m bars | 282, -7.8 / -3.9, +0.098 | 318, -8.8 / -11.0, -0.044 | 263, -7.6 / -6.8, -0.021 | 250, -12.8 / -12.0, -0.012 | 264, -12.5 / -18.2, -0.032 | 0/5 |
| e1_trend short, 5m bars | 256, -12.9 / -9.4, +0.028 | 266, -12.0 / -9.8, -0.136 | 260, -5.0 / -2.3, +0.032 | 287, -9.8 / -9.1, +0.062 | 279, -10.8 / -7.5, -0.025 | 0/5 |
| e1_reject long, 1m bars | 2143, -7.7 / -6.3, +0.034 | 2139, -10.6 / -8.7, +0.045 | 2075, -8.3 / -7.3, -0.005 | 1896, -10.0 / -8.0, +0.004 | 2107, -9.1 / -7.8, +0.034 | 0/5 |
| e1_reject short, 1m bars | 1842, -9.9 / -7.4, +0.012 | 1850, -11.1 / -8.7, +0.030 | 1965, -9.4 / -7.2, +0.013 | 1974, -9.3 / -7.8, +0.028 | 1939, -9.9 / -8.9, -0.003 | 0/5 |
| e1_reject long, 2m bars | 1506, -9.4 / -8.7, +0.028 | 1513, -11.6 / -9.2, +0.039 | 1427, -8.4 / -7.4, +0.005 | 1260, -10.0 / -8.9, -0.008 | 1431, -7.6 / -8.9, +0.040 | 0/5 |
| e1_reject short, 2m bars | 1192, -8.9 / -10.1, +0.014 | 1130, -9.8 / -10.1, +0.010 | 1324, -9.0 / -9.3, +0.015 | 1287, -10.7 / -8.5, +0.028 | 1299, -7.7 / -6.7, +0.019 | 0/5 |
| e1_reject long, 3m bars | 1143, -7.1 / -6.8, +0.029 | 1162, -10.6 / -9.2, +0.001 | 1073, -5.4 / -6.5, +0.017 | 893, -5.4 / -7.6, -0.011 | 1038, -7.3 / -7.4, +0.026 | 0/5 |
| e1_reject short, 3m bars | 896, -8.1 / -7.4, +0.009 | 828, -9.7 / -8.3, +0.002 | 1006, -7.7 / -6.1, +0.010 | 957, -8.6 / -9.5, -0.029 | 1021, -7.8 / -9.2, -0.009 | 0/5 |
| e1_reject long, 4m bars | 830, -8.8 / -8.0, +0.028 | 861, -9.8 / -9.2, -0.012 | 796, -3.9 / -6.2, +0.006 | 691, -8.0 / -7.2, -0.005 | 751, -7.7 / -8.3, +0.024 | 0/5 |
| e1_reject short, 4m bars | 663, -11.9 / -11.9, +0.005 | 558, -5.9 / -5.7, +0.034 | 701, -6.6 / -6.3, +0.026 | 709, -6.8 / -6.2, -0.004 | 739, -8.3 / -9.1, -0.002 | 0/5 |
| e1_reject long, 5m bars | 646, -8.0 / -9.0, +0.059 | 645, -9.6 / -9.3, +0.002 | 636, -12.7 / -8.6, +0.003 | 516, -8.7 / -8.3, +0.012 | 575, -9.0 / -7.3, +0.034 | 0/5 |
| e1_reject short, 5m bars | 474, -8.6 / -9.9, -0.003 | 457, -10.3 / -10.9, +0.040 | 566, -6.9 / -7.2, +0.028 | 569, -4.6 / -7.6, -0.000 | 581, -4.8 / -4.5, +0.039 | 0/5 |
| r2_rsi long, 1m bars | 320, +10.0 / +8.8, +0.021 ✓ | 308, +8.8 / +10.7, -0.070 | 330, +16.1 / +9.4, +0.030 ✓ | 383, +8.9 / +4.7, -0.077 | 348, +11.8 / +10.3, +0.097 ✓ | 3/5 |
| r2_rsi short, 1m bars | 224, -4.0 / -1.3, -0.109 | 210, +12.4 / +9.0, +0.013 ✓ | 225, +4.4 / +1.8, -0.061 | 187, +8.0 / +8.6, +0.051 ✓ | 214, +13.6 / +6.1, -0.057 | 2/5 |
| r2_rsi long, 2m bars | 205, +1.5 / +3.4, -0.014 | 175, +3.4 / +12.6, +0.067 | 229, +3.5 / +6.1, -0.001 | 255, -1.2 / +0.8, -0.115 | 229, +2.6 / +4.4, +0.069 ✓ | 1/5 |
| r2_rsi short, 2m bars | 145, -2.8 / -9.0, -0.082 | 131, -0.8 / +1.5, -0.044 | 153, +3.3 / +1.3, -0.066 | 110, +10.0 / -0.9, -0.078 | 128, +11.7 / +6.2, -0.049 | 0/5 |
| r2_rsi long, 3m bars | 168, -1.8 / -4.8, +0.016 | 148, +2.0 / +3.4, +0.099 ✓ | 196, +0.5 / -4.1, -0.048 | 213, -6.1 / +1.4, -0.079 | 198, +0.0 / -3.5, +0.037 | 1/5 |
| r2_rsi short, 3m bars | 109, -7.3 / +1.8, -0.122 | 93, -5.4 / -5.4, -0.107 | 116, -8.6 / -6.9, -0.091 | 82, -3.7 / +1.2, -0.028 | 116, -9.5 / -5.2, -0.016 | 0/5 |
| r2_rsi long, 4m bars | 134, +3.0 / +0.0, -0.015 | 113, -10.6 / +2.7, -0.002 | 160, +1.2 / +1.9, +0.020 | 179, -5.6 / -3.9, -0.085 | 172, -5.2 / -1.7, +0.035 | 0/5 |
| r2_rsi short, 4m bars | 97, -13.4 / -10.3, -0.056 | 75, -14.7 / -1.3, +0.015 | 105, -7.6 / -2.9, -0.008 | 72, -9.7 / -6.9, +0.029 | 86, -12.8 / -5.8, -0.070 | 0/5 |
| r2_rsi long, 5m bars | 103, +1.0 / +5.8, +0.101 ✓ | 111, -18.0 / -4.5, +0.021 | 145, -4.1 / -9.7, +0.008 | 163, -7.4 / -10.4, -0.111 | 152, -13.8 / -13.2, +0.025 | 1/5 |
| r2_rsi short, 5m bars | 87, -12.6 / -11.5, -0.023 | 73, -8.2 / -1.4, -0.043 | 85, -24.7 / -17.6, -0.090 | 59, -16.9 / +0.0, +0.082 | 79, -12.7 / -5.1, +0.035 | 0/5 |
| r2_rsi_sym long, 1m bars | 178, +11.8 / +10.7, +0.056 | 184, +10.3 / +6.5, -0.042 | 179, +11.2 / +11.2, +0.028 | 223, +12.1 / +6.3, -0.117 | 178, +11.2 / +11.2, +0.157 ✓ | 1/5 |
| r2_rsi_sym short, 1m bars | 224, -2.7 / +0.0, -0.109 | 210, +11.0 / +2.9, +0.013 ✓ | 225, +3.1 / +3.6, -0.061 | 187, +9.1 / +7.5, +0.051 ✓ | 214, +17.8 / +8.4, -0.057 | 2/5 |
| r2_rsi_sym long, 2m bars | 113, -3.5 / +2.7, +0.001 | 96, +1.0 / +1.0, -0.004 | 135, +9.6 / +8.9, +0.051 ✓ | 136, -2.2 / -1.5, -0.060 | 115, +2.6 / +6.1, +0.113 ✓ | 2/5 |
| r2_rsi_sym short, 2m bars | 145, +0.7 / -2.8, -0.082 | 131, +7.6 / +0.8, -0.044 | 153, +0.0 / +1.3, -0.066 | 110, +0.9 / -3.6, -0.078 | 128, +3.9 / +9.4, -0.049 | 0/5 |
| r2_rsi_sym long, 3m bars | 91, -2.2 / +4.4, +0.028 | 75, +0.0 / -5.3, +0.106 | 109, +2.8 / +5.5, -0.012 | 91, -8.8 / +13.2, -0.038 | 99, +1.0 / +1.0, +0.052 | 0/5 |
| r2_rsi_sym short, 3m bars | 109, -7.3 / -3.7, -0.122 | 93, +3.2 / -3.2, -0.107 | 116, -2.6 / -6.9, -0.091 | 82, +2.4 / -2.4, -0.028 | 116, -3.4 / +3.4, -0.016 | 0/5 |
| r2_rsi_sym long, 4m bars | 63, -12.7 / +0.0, +0.047 | 55, +1.8 / -1.8, -0.064 | 74, +8.1 / -1.4, +0.096 | 98, -12.2 / -12.2, -0.122 | 94, -5.3 / -2.1, +0.016 | 0/5 |
| r2_rsi_sym short, 4m bars | 97, -3.1 / -8.2, -0.056 | 75, -9.3 / -8.0, +0.015 | 105, -3.8 / -17.1, -0.008 | 72, -15.3 / -12.5, +0.029 | 86, -7.0 / -3.5, -0.070 | 0/5 |
| r2_rsi_sym long, 5m bars | 60, -6.7 / +1.7, +0.079 | 49, +0.0 / -4.1, -0.006 | 75, -8.0 / -2.7, +0.057 | 83, -9.6 / -4.8, -0.057 | 82, -2.4 / -6.1, +0.082 | 0/5 |
| r2_rsi_sym short, 5m bars | 87, -6.9 / -2.3, -0.023 | 73, -5.5 / -6.8, -0.043 | 85, -11.8 / -8.2, -0.090 | 59, -11.9 / -6.8, +0.082 | 79, -8.9 / +3.8, +0.035 | 0/5 |
| b3_touch long, 1m bars | 1953, +11.5 / +9.9, -0.001 | 1787, +13.2 / +10.6, -0.002 | 2017, +10.4 / +9.9, +0.020 ✓ | 1796, +8.4 / +7.5, -0.047 | 1923, +8.6 / +9.7, +0.001 | 1/5 |
| b3_touch short, 1m bars | 2140, +9.2 / +8.9, -0.017 | 1868, +10.9 / +8.3, -0.052 | 2024, +7.1 / +5.9, -0.004 | 1748, +9.3 / +8.7, +0.002 | 1992, +9.9 / +10.7, -0.012 | 0/5 |
| b3_touch long, 2m bars | 1357, +11.5 / +11.2, -0.008 | 1244, +13.9 / +14.5, -0.015 | 1374, +10.8 / +9.8, +0.012 ✓ | 1210, +9.1 / +10.6, -0.050 | 1324, +10.8 / +12.4, +0.014 | 1/5 |
| b3_touch short, 2m bars | 1499, +10.1 / +8.1, -0.026 | 1280, +13.4 / +9.3, -0.043 | 1362, +11.2 / +11.4, -0.005 | 1163, +13.6 / +10.8, +0.008 ✓ | 1336, +10.1 / +8.5, -0.017 | 1/5 |
| b3_touch long, 3m bars | 1095, +11.9 / +7.0, -0.026 | 1002, +10.4 / +11.1, +0.005 | 1107, +14.0 / +12.1, +0.031 ✓ | 979, +8.7 / +6.1, -0.048 | 1106, +8.2 / +11.6, +0.035 ✓ | 2/5 |
| b3_touch short, 3m bars | 1265, +9.0 / +6.6, -0.022 | 1062, +7.9 / +8.9, -0.055 | 1131, +9.2 / +7.5, -0.033 | 954, +13.3 / +8.4, +0.015 | 1067, +8.5 / +7.6, -0.039 | 0/5 |
| b3_touch long, 4m bars | 785, +7.0 / +5.6, -0.030 | 706, +8.4 / +8.2, +0.033 | 787, +10.8 / +7.4, +0.026 ✓ | 714, +5.6 / +4.1, -0.073 | 784, +9.1 / +6.8, +0.004 | 1/5 |
| b3_touch short, 4m bars | 910, +9.8 / +5.6, -0.008 | 749, +11.1 / +8.7, -0.054 | 801, +8.7 / +7.1, -0.026 | 672, +7.9 / +8.8, +0.001 | 776, +12.0 / +7.1, -0.027 | 0/5 |
| b3_touch long, 5m bars | 635, +8.2 / +4.3, -0.017 | 574, +9.8 / +5.6, +0.054 ✓ | 659, +10.9 / +12.6, +0.027 ✓ | 631, +7.0 / +5.4, -0.070 | 685, +4.8 / +7.0, +0.017 | 2/5 |
| b3_touch short, 5m bars | 789, +7.0 / +5.4, -0.041 | 665, +11.9 / +7.7, -0.055 | 727, +6.2 / +5.8, -0.039 | 604, +5.8 / +7.9, -0.029 | 679, +5.7 / +6.8, -0.047 | 0/5 |
| b3_reentry long, 1m bars | 767, +10.7 / +11.1, +0.015 ✓ | 789, +13.3 / +12.8, -0.004 | 799, +14.6 / +11.8, +0.049 ✓ | 794, +11.7 / +9.3, -0.020 | 782, +11.9 / +10.5, +0.013 ✓ | 3/5 |
| b3_reentry short, 1m bars | 777, +12.5 / +6.4, -0.044 | 755, +12.7 / +9.8, -0.078 | 697, +12.2 / +8.9, -0.014 | 759, +9.7 / +10.8, +0.000 | 746, +12.3 / +9.9, -0.004 | 0/5 |
| b3_reentry long, 2m bars | 425, +8.9 / +5.2, -0.043 | 462, +12.3 / +10.6, +0.021 | 445, +18.0 / +13.9, +0.025 ✓ | 477, +11.9 / +6.9, -0.053 | 460, +14.1 / +10.0, +0.024 | 1/5 |
| b3_reentry short, 2m bars | 467, +9.4 / +7.1, -0.040 | 446, +13.9 / +8.7, -0.080 | 423, +5.9 / +7.6, -0.031 | 434, +13.1 / +4.1, +0.029 ✓ | 424, +13.0 / +6.6, -0.078 | 1/5 |
| b3_reentry long, 3m bars | 321, +5.3 / +6.9, -0.039 | 318, +4.1 / +4.1, +0.006 | 344, +9.3 / +9.3, +0.018 ✓ | 340, +13.2 / +6.2, -0.074 | 347, +6.3 / +7.8, +0.020 | 1/5 |
| b3_reentry short, 3m bars | 341, +7.6 / +6.5, -0.051 | 321, +10.0 / +8.4, +0.005 ✓ | 319, +8.5 / +7.5, -0.019 | 316, +7.0 / +3.8, -0.035 | 313, +10.9 / +4.8, -0.075 | 1/5 |
| b3_reentry long, 4m bars | 252, +3.2 / +0.0, -0.052 | 239, +2.5 / +4.2, +0.073 | 248, +4.4 / +1.2, -0.022 | 272, +4.8 / -0.7, -0.066 | 267, +8.2 / +10.1, +0.101 ✓ | 1/5 |
| b3_reentry short, 4m bars | 273, +2.9 / +4.4, -0.025 | 253, +7.5 / +3.6, -0.028 | 245, +2.9 / +1.2, -0.025 | 245, +6.1 / +9.0, +0.005 | 236, +10.6 / +6.8, -0.035 | 0/5 |
| b3_reentry long, 5m bars | 221, -1.4 / +7.2, +0.017 | 213, +0.5 / +5.6, +0.072 | 229, -2.2 / -1.3, -0.006 | 246, -1.2 / -0.4, -0.092 | 235, +2.1 / +10.6, +0.092 ✓ | 1/5 |
| b3_reentry short, 5m bars | 247, +1.6 / -0.8, +0.006 | 235, +3.0 / +8.1, +0.001 ✓ | 233, -8.2 / +1.3, -0.076 | 218, +5.0 / +5.0, +0.024 ✓ | 230, -1.7 / -2.2, -0.024 | 2/5 |
| orb15 long, 1m bars | 84, -17.9 / -8.3, +0.031 | 62, -11.3 / -17.7, +0.202 | 58, -5.2 / -3.4, +0.085 | 46, -23.9 / -6.5, +0.076 | 53, -7.5 / +7.5, +0.041 | 0/5 |
| orb15 short, 1m bars | 62, -17.7 / -11.3, +0.058 | 51, -13.7 / -17.6, -0.070 | 55, -14.5 / -14.5, +0.078 | 55, -5.5 / +1.8, +0.106 | 57, -26.3 / -12.3, +0.040 | 0/5 |
| orb15 long, 5m bars | 19, -10.5 / -26.3, +0.235 | 8, +0.0 / -25.0, -0.347 | 9, -44.4 / -22.2, -0.245 | 3, +33.3 / +66.7, +0.371 ✓ | 6, +0.0 / -16.7, +0.059 | 1/5 |
| orb15 short, 5m bars | 12, -41.7 / -8.3, +0.052 | 19, -15.8 / -10.5, +0.022 | 12, +0.0 / -8.3, +0.197 | 8, +25.0 / +0.0, +0.103 | 7, +28.6 / -28.6, -0.175 | 0/5 |
| orb30 long, 1m bars | 76, -10.5 / -17.1, +0.047 | 64, -12.5 / -25.0, +0.110 | 63, -7.9 / +4.8, +0.110 | 46, -10.9 / -4.3, -0.056 | 50, -16.0 / -4.0, +0.070 | 0/5 |
| orb30 short, 1m bars | 65, -3.1 / -10.8, -0.017 | 47, -19.1 / -6.4, +0.193 | 64, -12.5 / -15.6, +0.016 | 62, -1.6 / -8.1, +0.040 | 55, -14.5 / -10.9, +0.065 | 0/5 |
| orb30 long, 5m bars | 22, -22.7 / -9.1, +0.181 | 9, -55.6 / -44.4, -0.481 | 8, -12.5 / -37.5, -0.049 | 3, +0.0 / +33.3, +0.419 | 10, -10.0 / -40.0, +0.021 | 0/5 |
| orb30 short, 5m bars | 19, -15.8 / -15.8, -0.009 | 16, -6.2 / -12.5, -0.016 | 15, -6.7 / -20.0, +0.101 | 11, -18.2 / -45.5, -0.279 | 10, -20.0 / -20.0, -0.137 | 0/5 |
| gap0.5_cont long | 74, +6.8 / +9.5, +0.088 ✓ | 125, +1.6 / -4.8, -0.055 | 77, -7.8 / +5.2, +0.007 | 90, -15.6 / +4.4, +0.209 | 89, +1.1 / -2.2, +0.042 | 1/5 |
| gap0.5_cont short | 56, -7.1 / +5.4, -0.064 | 59, +13.6 / +3.4, +0.166 ✓ | 65, -10.8 / -1.5, -0.119 | 96, -3.1 / -2.1, +0.207 | 70, +1.4 / +11.4, +0.012 ✓ | 2/5 |
| gap0.5_fill long | 56, +7.1 / -10.7, +0.064 | 59, -13.6 / -5.1, -0.166 | 65, +10.8 / -1.5, +0.119 | 96, +1.0 / -6.2, -0.207 | 70, -12.9 / -2.9, -0.012 | 0/5 |
| gap0.5_fill short | 74, +2.7 / +1.4, -0.088 | 125, +0.8 / +5.6, +0.055 ✓ | 77, +3.9 / +1.3, -0.007 | 90, +6.7 / -11.1, -0.209 | 89, -2.2 / -9.0, -0.042 | 1/5 |
| gap1_cont long | 39, +7.7 / +15.4, +0.139 ✓ | 89, -4.5 / +3.4, +0.047 | 41, -2.4 / -7.3, +0.055 | 64, -12.5 / +3.1, +0.274 | 54, +7.4 / +0.0, +0.316 | 1/5 |
| gap1_cont short | 30, -3.3 / +10.0, +0.091 | 44, +9.1 / +4.5, +0.096 ✓ | 45, +8.9 / +11.1, -0.220 | 70, -2.9 / +0.0, +0.258 | 41, -2.4 / +19.5, +0.007 | 1/5 |
| gap1_fill long | 30, -3.3 / -3.3, -0.091 | 44, -13.6 / +0.0, -0.096 | 45, -2.2 / -4.4, +0.220 | 70, +0.0 / -1.4, -0.258 | 41, +4.9 / -17.1, -0.007 | 0/5 |
| gap1_fill short | 39, -5.1 / -12.8, -0.139 | 89, -2.2 / -1.1, -0.047 | 41, +12.2 / +9.8, -0.055 | 64, -4.7 / -12.5, -0.274 | 54, +0.0 / -5.6, -0.316 | 0/5 |
| first_half_hour long | 91, -12.1 / -12.1, -0.003 | 90, -16.7 / -25.6, +0.070 | 86, -5.8 / -9.3, +0.066 | 90, -20.0 / -6.7, +0.175 | 91, -8.8 / -17.6, +0.015 | 0/5 |
| first_half_hour short | 74, -16.2 / -13.5, -0.037 | 86, -18.6 / -24.4, -0.129 | 78, -12.8 / -12.8, +0.069 | 99, -8.1 / -8.1, +0.084 | 85, -21.2 / -12.9, +0.061 | 0/5 |
