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

The year-by-year tables for every row are in the full report.

---

Full per-trade tables: [history/2026-10-28-t10-research-bench.md](history/2026-10-28-t10-research-bench.md)
