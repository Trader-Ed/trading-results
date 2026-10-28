# T12: "stocks in play" momentum on the daily top-10 gappers (2019-2023)

**Comparisons: 6 setup × bar-size rows judged by the pass bar** (3 setups × 5- and 2-minute bars; the "both" rows are shown for reference). At 3 standard errors one-sided, about 0.01 would clear the control gap by chance.

## Findings

**PASS: none.** No setup clears the bar at either bar size, and no share-trading candidate goes to the partners.

- **sip_orb (9,463 trades): loses after costs every year.** The 2R trade averages -0.034R (5-minute bars) and -0.039R (2-minute) after costs, negative in all 5 years. Before costs it is +0.026R; costs are about 0.06R a trade, because the first 5-minute bar of a gapper is wide (median R 4.6% of price). Trading with the gap beats trading against it by +0.04R, z +1.6 and +1.2: below the 3 needed. It reaches +2R before -1R only 9-12% of the time, and most trades are still open at 15:30.
- **sip_retrace (30,928 trades): loses more, because its stops are tight.** The 2R trade averages -0.121R (5-minute) and -0.105R (2-minute) after costs, negative in all 5 years. Before costs it is +0.05R, but costs take 0.16-0.17R a trade (median R 1.5% of price; on 15-18% of trades costs exceed 0.25R). With the gap beats against it by +0.05R and +0.04R, z +2.2 and +1.3. The year-by-year z fades from +2.8 in 2019 to -0.8 in 2021.
- **sip_consol (35 trades in 5 years): can't be judged as specified.** The base limit, 0.5 × ATR(14) / 13, is about 0.14% of price on these stocks. Their median 5-minute bar on a gap day spans 0.77%, more than five times that. The tightest 3-bar stretch of the morning fits under the limit on only 0.9% of stock-days. On stocks in play, ATR/13 is not a typical 5-minute bar's range. A base sized to today's own bars (for example a share of the opening 5-minute bar's range) would be a new rule, and a partner decision.
- **Direction.** In every row, trading with the gap does a little better than trading against it (+0.04 to +0.05R per trade) and better than a random direction (+0.01 to +0.04R). The tilt is consistent in sign but small: about two-thirds of ORB's costs, and under a third of the retrace's.
- **Larger gaps lose less (not tested by the pass bar).** Across all setups, the 2R trade after costs is -0.142R on 4-8% gaps (23,794 trades), -0.048R on 8-15% gaps and -0.004R on gaps over 15% (6,008 trades). sip_orb is +0.007R on 8-15% gaps and +0.011R over 15%. That is about zero, and it was found after looking, so it would need its own pre-set test. No price band is positive for sip_retrace.
- **Survivorship.** Alpaca's asset list misses most delisted symbols (see the universe section), so the universe leans toward names that survived. How that moves intraday results is not known; the missing names are mostly companies that later failed or were bought.

## PASS list

None.

## Universe and data

| Step | Count |
|---|---|
| Alpaca asset list, NASDAQ/NYSE/AMEX, kept as common stock (ETFs, ETNs, funds, warrants, units, rights, preferreds and notes removed by name) | 5,657 active + 937 inactive = 6,594 symbols |
| Symbols with daily bars 2018-11 to 2023-12 | 4,713 active + 835 inactive |
| Stock-days passing the daily prefilter (price $5-$500, 20-day volume ≥ 1M, daily open gap ≥ 2.5%) | 120,098 (2,798 symbols) |
| ... with a 9:30 gap ≥ 4% | 49,909 |
| ... and first-5-minute volume ≥ 2× its 20-day average | 19,672 |
| Selected: top 10 by volume ratio each day | **10,527 stock-days**, 1,979 symbols, 1,256 of 1,258 sessions (median 10 a day; median gap 7.0%, median volume ratio 6.2×) |
| 1-minute bars downloaded (raw, 9:30-16:00, selected stock-days only) | **10,516 stock-days**, 4.05 million bars (11 had no bars) |
| Skipped: FOMC decision days | 356 stock-days on 40 days |
| Traded | 10,160 stock-days; 9,855 gave at least one signal |

**Delisted symbols.** Alpaca serves bars for delisted symbols when asked by name (TWTR, BBBY, SIVB, ATVI all return data up to their last day), but its asset list keeps only some of them: 2 of 10 well-known 2019-2023 delistings checked are in it (XLNX, CERN; not TWTR, ATVI, SIVB, BBBY, FRC, CTXS, SBNY, DISCA). So the universe includes 522 selected stock-days on now-inactive symbols (192 in 2019 falling to 5 in 2023), but misses gappers that later delisted and dropped out of Alpaca's list. Survivorship bias remains, most in later years. Symbols renamed since (FB → META) are covered under their current symbol.

**Data checks.** Alpaca's daily open is the official open, within 0.1% of the 9:30 one-minute open on 91-100% of days (checked on the bench's 9 names), so the 2.5% prefilter loses almost nothing; the 4% gap uses the first trade from 9:30. 4 stock-days were dropped because Alpaca's split factor changes overnight (the adjusted prior close does not match today's prices, e.g. NVS on 2019-04-09). A few selected gaps come from spin-offs or liquidating payouts rather than news (e.g. BHVN 2022-10-04, AABA 2019-09-24); their intraday bars are real, so they stay. Downloads: daily bars 16 min (89 MB), first-5-minute bars 36 min (21 MB), 1-minute bars 5 min (51 MB); 120 MB in data/bench/t12. The run itself takes about 45 s (two jobs).

## Results by setup (2R trade is the pass bar's trade)

| Setup | Bars | Trades | Days | Avg R after costs (2R trade) | ± SE | Hit +2R before -1R | vs opposite direction (R) | z | vs random direction (R) | z | Avg R, 1R trade | Avg R, 3R trade | Years with avg R > 0 | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sip_orb | 5-min | 5172 | 1182 | -0.034 | 0.015 | 9.0% | +0.043 | +1.6 | +0.024 | +1.3 | -0.041 | -0.034 | 0/5 | FAIL |
| sip_orb | 2-min | 4291 | 1169 | -0.039 | 0.017 | 11.8% | +0.038 | +1.2 | +0.036 | +1.7 | -0.047 | -0.031 | 0/5 | FAIL |
| sip_orb | both | 9463 | 1192 | -0.036 | 0.015 | 10.2% | +0.041 | +1.5 | +0.029 | +1.8 | -0.044 | -0.033 | 0/5 | FAIL |
| sip_retrace | 5-min | 20175 | 1215 | -0.121 | 0.013 | 26.4% | +0.053 | +2.2 | +0.030 | +2.0 | -0.153 | -0.106 | 0/5 | FAIL |
| sip_retrace | 2-min | 10753 | 1204 | -0.105 | 0.016 | 30.0% | +0.037 | +1.3 | +0.014 | +0.8 | -0.127 | -0.092 | 0/5 | FAIL |
| sip_retrace | both | 30928 | 1216 | -0.115 | 0.012 | 27.7% | +0.048 | +2.2 | +0.024 | +1.9 | -0.144 | -0.101 | 0/5 | FAIL |
| sip_consol | 5-min | 27 | 22 | -0.372 | 0.297 | 29.6% | +0.207 | +0.4 | -0.157 | -0.5 | -0.520 | -0.211 | 2/5 | FAIL |
| sip_consol | 2-min | 8 | 8 | +0.299 | 0.523 | 50.0% | +1.280 | +1.6 | +0.905 | +1.2 | +0.077 | +0.799 | 3/5 | FAIL |
| sip_consol | both | 35 | 27 | -0.218 | 0.259 | 34.3% | +0.452 | +1.1 | +0.086 | +0.3 | -0.384 | +0.020 | 3/5 | FAIL |

## By year (2R trade, R after costs; z vs the opposite direction)

| Setup | Bars | 2019: trades, avg R, vs opposite (z) | 2020: trades, avg R, vs opposite (z) | 2021: trades, avg R, vs opposite (z) | 2022: trades, avg R, vs opposite (z) | 2023: trades, avg R, vs opposite (z) |
|---|---|---|---|---|---|---|
| sip_orb | 5-min | 781, -0.011 (+1.6) | 1110, -0.037 (+0.3) | 1145, -0.035 (+0.8) | 1127, -0.048 (+0.3) | 1009, -0.034 (+0.8) |
| sip_orb | 2-min | 654, -0.058 (+0.4) | 903, -0.062 (-0.5) | 984, -0.047 (+0.4) | 926, -0.001 (+1.4) | 824, -0.029 (+0.9) |
| sip_orb | both | 1435, -0.032 (+1.1) | 2013, -0.048 (-0.1) | 2129, -0.041 (+0.7) | 2053, -0.027 (+0.9) | 1833, -0.032 (+0.9) |
| sip_retrace | 5-min | 3077, -0.086 (+2.7) | 4411, -0.084 (+1.5) | 4475, -0.120 (-0.1) | 4232, -0.174 (-0.5) | 3980, -0.133 (+1.4) |
| sip_retrace | 2-min | 1533, -0.074 (+1.9) | 2381, -0.094 (+0.9) | 2402, -0.125 (-1.4) | 2241, -0.093 (+0.9) | 2196, -0.127 (+0.8) |
| sip_retrace | both | 4610, -0.082 (+2.8) | 6792, -0.088 (+1.5) | 6877, -0.122 (-0.8) | 6473, -0.146 (+0.1) | 6176, -0.131 (+1.4) |
| sip_consol | 5-min | 2, -1.039 | 14, -0.843 (-0.8) | 4, -0.439 | 4, +0.150 | 3, +1.665 |
| sip_consol | 2-min | 1, +0.823 | 5, -0.400 | 1, +1.936 | 0 | 1, +1.635 |
| sip_consol | both | 3, -0.418 | 19, -0.726 (-0.6) | 5, +0.036 | 4, +0.150 | 4, +1.657 |

## Hit rates: target reached before -1R (signal / opposite direction / random direction)

| Setup | Bars | Hit +1R / opposite / random | Hit +2R / opposite / random | Hit +3R / opposite / random |
|---|---|---|---|---|
| sip_orb | 5-min | 30.1% / 27.3% / 28.6% | 9.0% / 6.3% / 7.7% | 3.2% / 2.1% / 2.6% |
| sip_orb | 2-min | 35.1% / 33.0% / 33.1% | 11.8% / 9.1% / 10.2% | 4.7% / 3.1% / 4.0% |
| sip_orb | both | 32.3% / 29.9% / 30.6% | 10.2% / 7.6% / 8.8% | 3.8% / 2.5% / 3.3% |
| sip_retrace | 5-min | 47.7% / 46.2% / 46.7% | 26.4% / 24.6% / 25.3% | 14.7% / 12.9% / 13.7% |
| sip_retrace | 2-min | 50.2% / 47.1% / 48.3% | 30.0% / 28.5% / 29.1% | 18.2% / 16.7% / 17.5% |
| sip_retrace | both | 48.6% / 46.5% / 47.3% | 27.7% / 26.0% / 26.6% | 15.9% / 14.2% / 15.0% |
| sip_consol | 5-min | 37.0% / 40.7% / 40.7% | 29.6% / 11.1% / 22.2% | 22.2% / 7.4% / 11.1% |
| sip_consol | 2-min | 75.0% / 25.0% / 37.5% | 50.0% / 12.5% / 25.0% | 50.0% / 12.5% / 25.0% |
| sip_consol | both | 45.7% / 37.1% / 40.0% | 34.3% / 11.4% / 22.9% | 28.6% / 8.6% / 14.3% |

## Distribution of R outcomes (after costs)

| Setup | Bars | Trade | Target | Stop | Out at 15:30 | Avg R at 15:30 exits | Gross avg R | Cost avg R | Net R: 10th / 25th / median / 75th / 90th pct |
|---|---|---|---|---|---|---|---|---|---|
| sip_orb | 5-min | 1R | 30% | 27% | 43% | -0.07 | +0.020 | 0.061 | -1.06 / -1.02 / -0.04 / +0.90 / +0.96 |
| sip_orb | 5-min | 2R | 9% | 29% | 62% | +0.17 | +0.027 | 0.061 | -1.06 / -1.03 / -0.12 / +0.55 / +1.49 |
| sip_orb | 5-min | 3R | 3% | 30% | 67% | +0.29 | +0.027 | 0.061 | -1.06 / -1.03 / -0.13 / +0.52 / +1.25 |
| sip_orb | 2-min | 1R | 35% | 33% | 32% | -0.06 | +0.017 | 0.063 | -1.07 / -1.03 / -0.02 / +0.93 / +0.96 |
| sip_orb | 2-min | 2R | 12% | 36% | 52% | +0.24 | +0.025 | 0.063 | -1.08 / -1.04 / -0.19 / +0.67 / +1.87 |
| sip_orb | 2-min | 3R | 5% | 37% | 59% | +0.38 | +0.033 | 0.063 | -1.08 / -1.04 / -0.20 / +0.60 / +1.48 |
| sip_retrace | 5-min | 1R | 48% | 46% | 6% | -0.09 | +0.016 | 0.169 | -1.23 / -1.13 / +0.05 / +0.86 / +0.92 |
| sip_retrace | 5-min | 2R | 26% | 56% | 18% | +0.29 | +0.048 | 0.169 | -1.26 / -1.15 / -1.06 / +1.58 / +1.88 |
| sip_retrace | 5-min | 3R | 15% | 58% | 27% | +0.62 | +0.063 | 0.169 | -1.27 / -1.16 / -1.07 / +0.85 / +2.78 |
| sip_retrace | 2-min | 1R | 50% | 47% | 3% | -0.09 | +0.030 | 0.157 | -1.21 / -1.12 / +0.37 / +0.88 / +0.93 |
| sip_retrace | 2-min | 2R | 30% | 60% | 10% | +0.36 | +0.052 | 0.157 | -1.24 / -1.14 / -1.07 / +1.75 / +1.90 |
| sip_retrace | 2-min | 3R | 18% | 63% | 18% | +0.73 | +0.065 | 0.157 | -1.25 / -1.15 / -1.08 / +1.00 / +2.85 |
| sip_consol | 5-min | 1R | 37% | 41% | 22% | -0.85 | -0.067 | 0.452 | -1.55 / -1.22 / -0.98 / +0.51 / +0.86 |
| sip_consol | 5-min | 2R | 30% | 48% | 22% | -0.85 | +0.081 | 0.453 | -1.55 / -1.23 / -1.05 / +0.99 / +1.86 |
| sip_consol | 5-min | 3R | 22% | 48% | 30% | -0.43 | +0.242 | 0.452 | -1.55 / -1.23 / -1.05 / +0.81 / +2.76 |
| sip_consol | 2-min | 1R | 75% | 25% | 0% | - | +0.500 | 0.423 | -1.17 / -0.40 / +0.37 / +0.72 / +0.92 |
| sip_consol | 2-min | 2R | 50% | 38% | 12% | +0.02 | +0.723 | 0.424 | -1.40 / -1.15 / +0.42 / +1.71 / +1.92 |
| sip_consol | 2-min | 3R | 50% | 38% | 12% | +0.02 | +1.223 | 0.424 | -1.40 / -1.15 / +0.92 / +2.71 / +2.92 |

## Risk size and costs

| Setup | Bars | Median R (% of price) | Median R ($) | Median cost per trade (R) | Share of trades with cost > 0.25R |
|---|---|---|---|---|---|
| sip_orb | 5-min | 4.57% | 1.09 | 0.044 | 2% |
| sip_orb | 2-min | 4.23% | 1.03 | 0.046 | 2% |
| sip_retrace | 5-min | 1.48% | 0.37 | 0.132 | 18% |
| sip_retrace | 2-min | 1.60% | 0.40 | 0.121 | 15% |
| sip_consol | 5-min | 1.18% | 0.12 | 0.288 | 52% |
| sip_consol | 2-min | 1.08% | 0.13 | 0.358 | 62% |

## By gap size (2R trade)

| Setup (both bar sizes) | 4-8%: trades, avg R, hit +2R | 8-15%: trades, avg R, hit +2R | over 15%: trades, avg R, hit +2R |
|---|---|---|---|
| sip_orb | 5594, -0.067, 10% | 2444, +0.007, 10% | 1425, +0.011, 12% |
| sip_retrace | 18186, -0.165, 27% | 8174, -0.065, 28% | 4568, -0.006, 29% |
| sip_consol | 14, +0.085, 43% | 6, +0.730, 67% | 15, -0.881, 13% |
| all setups | 23794, -0.142, 23% | 10624, -0.048, 24% | 6008, -0.004, 25% |

## By price band (prior close; 2R trade)

| Setup (both bar sizes) | $5-10: trades, avg R, hit +2R | $10-20: trades, avg R, hit +2R | $20-50: trades, avg R, hit +2R | $50-100: trades, avg R, hit +2R | $100-500: trades, avg R, hit +2R |
|---|---|---|---|---|---|
| sip_orb | 2135, -0.101, 12% | 2238, +0.033, 13% | 2642, -0.072, 9% | 1290, -0.026, 7% | 1158, +0.019, 9% |
| sip_retrace | 6598, -0.169, 28% | 7227, -0.102, 28% | 8987, -0.106, 27% | 4216, -0.095, 27% | 3900, -0.092, 27% |
| sip_consol | 13, -0.257, 31% | 5, +0.429, 60% | 10, -0.388, 30% | 6, -0.566, 17% | 1, +0.823, 100% |
| all setups | 8746, -0.152, 24% | 9470, -0.070, 25% | 11639, -0.098, 23% | 5512, -0.079, 23% | 5059, -0.067, 23% |

## Method

- Universe each day (known by 9:35): price $5-$500 at the prior close; 20-day average volume >= 1M shares; |gap| >= 4% (first trade from 9:30 vs the prior close); first-5-minute volume >= 2x its 20-day average; top 10 by that ratio. Research years 2019-2023 only; FOMC decision days skipped.
- Signals only in the gap's direction, deciding at a bar's close: 5-minute bars (entries 9:35-11:30) and 2-minute bars (entries 9:35-10:00), aligned to 9:30. EMA 9 and SMA 20 use today's bars only (SMA over the bars so far until there are 20).
- sip_orb: the first close beyond the 9:30-9:35 range high (gap up) or low (gap down); stop at the other side of that range; one per stock-day.
- sip_retrace: a bar's low (high for shorts) reaches the 9 EMA or 20 SMA after the prior bar closed on the trend side of it; then a later bar closes beyond the prior bar's high (low); stop $0.01 beyond the pullback's extreme since the touch. A new touch is needed after each entry.
- sip_consol: the longest run of >= 3 bars ending at the prior bar with total range <= 0.5 x ATR(14 days) / 13 and every close on the trend side of the 9 EMA, starting after the last entry; a close beyond the base is the entry; stop $0.01 beyond its far side. Same threshold on 2-minute bars.
- Race: R = |entry - stop|; 1-minute bars after the entry close up to 15:30 (12:30 on half days). A minute that reaches both the target and -1R counts as the stop; a stop the price opens through fills at that minute's open. Three trades per signal (targets 1R, 2R, 3R; out at 15:30 if neither). Raw (as traded) prices; costs 0.05% of price per side plus $0.01 per share each way, in R.
- Controls: the same stock, entry moment and R, the opposite direction; and a random direction (seed 7). Gaps are paired per signal; standard errors are clustered by day.

Pass bar (set before the run): at least 300 trades per setup and bar size; the 2R trade's average R after costs positive in at least 4 of 5 years; the 2R trade beating the opposite-direction control (paired, per signal) by at least 3 standard errors clustered by day; and positive overall.
