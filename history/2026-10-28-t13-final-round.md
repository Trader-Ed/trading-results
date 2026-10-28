FINAL ROUND OUTCOME: PASS

# T13: the final focused round (2016-2018 confirmation; research years 2019-2023)

**Comparisons judged: 10** (Part A: 1 strategy; Part B: 5 leads; Part C: 4 gap × bar-size rows). At 3 standard errors one-sided, about 0.01 would pass by chance.

## Findings

**The outcome is PASS by the pass bars as written, and only through Part B, the T11 box races.** Three box rows confirm on 2016-2018. But a fuller version of the same measure (below) does not confirm them, and their size is below the cost of trading shares. Parts A and C do not pass.

### Part A: the paper's strategy: NO PASS

- **Before costs it works; after our costs it does not.** 32,232 trades in 2016-2023 (11,749 in 2016-2018, 20,483 in 2019-2023). Average per trade: **+0.34R before costs**, **+0.28R with the paper's $0.0035-a-share commission**, but **-0.16R after our costs** (z -5.5). After our costs it is negative in every year but 2022 (+0.01R), and -0.23R over 2016-2018.
- **The stop is tiny, so per-share costs dominate.** R is 10% of the daily ATR, a median 0.34% of price. Our costs (0.05% a side plus $0.01 a share each way) take about half an R per trade.
- **Direction is real at that moment.** Trading in the first candle's direction beats the opposite direction by +0.31R per trade (z +8.6) and a random direction by +0.17R (z +7.0), in every year. It is the one check that passes.
- **The result rests on what happens inside the entry minute.** With 1-minute bars we cannot tell whether a minute's low came before or after the breakout fill. The main run counts the entry minute as stopped only when it closes beyond the stop. Counting any touch instead gives **-0.72R after our costs**. The truth lies between, so even the before-costs edge is uncertain.
- **Ignore the account returns before costs and at the paper's commission.** Those accounts compound 1% risk on a 0.3% stop at 4× leverage with the generous entry-minute rule, giving figures in the thousands of percent a year. The paper reports about 1,600% over all of 2016-2023, net. After our costs, the account loses almost everything in both periods (worst drop -100%).

### Part B: the T11 leads on 2016-2018: three of five pass by the bar as set

- **kc_mom_p6_m2 long: FAIL.** 2,742 signals in all9: 52.2% move our way at 10 minutes against 48.8% for the control (z +2.1), and 53.9% against 48.5% at 30 minutes (z +3.1). Every year is positive and SPY has the same sign, but 10 minutes misses z 3.
- **Box races, by T11's measure: PASS for box_k0.25_c0 long (z +3.7), box_k0.25_c1 long (z +4.6) and box_k0.25_c1 short (z +4.3); FAIL for box_k0.25_c0 short (z +2.7).** The passing rows beat the control by +0.04% to +0.06% of price per race, positive in each of 2016, 2017 and 2018, and SPY has the same sign (z +0.2 to +2.0).
- **Check: the measure scores races that reach neither target nor stop as 0.** Those races end lower after a box signal than after the control: -0.05% to -0.12% at 60 minutes, against -0.03% to -0.08%. Scoring them at their actual 60-minute move, the gap shrinks to +0.02% to +0.04% per race and z falls to **+1.7 to +2.7: none reaches 3**. In SPY it is -0.3 to +1.6. Same-bar outcomes never happened, so that choice does not matter.
- **Size.** Even by T11's measure, +0.04% to +0.06% of price per race is below what a round trip in these shares costs (about 0.1% plus 2 cents a share), and it is too small for 0DTE options. Whether this counts as a usable result is a partner decision. Nothing was changed after seeing the data.

### Part C: big-gap sip_orb on 2016-2018: NO PASS

- **Gaps of at least 8%:** +0.046R (5-minute, 765 trades, z +1.3) and +0.054R (2-minute, 614 trades, z +1.2) after costs. Positive in 2016 and 2017, about zero in 2018. Same direction as in 2019-2023, but nowhere near 3 standard errors.
- **Gaps of at least 15%:** 217 and 171 trades, short of 300, with averages of -0.007R and +0.025R (z about 0).

### Data notes

- **2016 start:** Alpaca's SIP history starts in January 2016, so 2016 has no warm-up before it. The paper's universe starts on 2016-01-25 (after 14 sessions), T12's on 2016-02-02 (after 20), and T11's daily ATR for the box warms up during January 2016.
- **Data:** 39,960 paper stock-days (top 20 a day, 2,576 symbols; median relative volume 4.7×) and 4,644 T12 stock-days for 2016-2018 were downloaded, 167 MB in data/bench/t13.
- **FOMC days:** the 24 FOMC decision days of 2016-2018 are taken from the Federal Reserve's website and added to the bench config. They are skipped in Parts B and C, but not in Part A, because the paper does not skip them.
- **Holdout:** 2024-2025 was not touched.

## Paper rules: what was used, and where it differs

The paper (Zarattini, Barbon and Aziz, "A Profitable Day Trading Strategy For The U.S. Equity Market", Swiss Finance Institute Research Paper 24-98, SSRN 4729284) could not be read directly: SSRN refused automated access (HTTP 403) and no other full copy was found. Its rules below come from CXO Advisory's review, which quotes the paper's wording, checked against QuantConnect's published replication notes. Where these sources state a rule, the paper's version was used.

| Rule | Partner instruction | Paper (as quoted) | Used in T13 |
|---|---|---|---|
| Price filter | price above $5 | **opening price** above $5 | paper: today's official open above $5 |
| Volume filter | 14-day average volume ≥ 1M shares | same | same |
| Volatility filter | 14-day ATR above $0.50 | same | same (Wilder ATR on daily bars, through the prior day) |
| In play | first-5-minute volume ≥ 1× its prior 14-day average | relative volume ≥ 100% | same |
| Selection | top 20 by that ratio | top 20 | same |
| Direction | first 5-minute candle up → long, down → short, flat → none | long on positive opens, short on negative opens (first 5-minute candle) | same |
| Entry | trading through the first candle's high/low after 9:35 | stop order at the opening-range high/low | same; filled at the level, or at the minute's open if it opens beyond |
| Stop | 10% of the 14-day ATR from the entry | 10% ATR from the executed entry price | same |
| Exit | stop, or the 15:59 close | stop, or the market close | close of the 15:59 minute (the closing auction is not modelled) |
| Sizing | 1% risk per trade, total size ≤ 4× the account | 1% of capital at risk per trade, 4× leverage cap | same, sized on the day's opening equity |
| Starting capital | not stated | **$25,000** | $25,000 |
| Costs | 0.05% of price per side + $0.01 per share | **$0.0035 per share commission** (Interactive Brokers Pro Tiered) | all three shown: before costs, paper's commission, ours |
| Universe | US common stocks | **over 7,000 US stocks, 2016-2023** | Alpaca's list (6,594 common stocks, active and part of the inactive); most delisted names missing |
| Period | 2016-2018 and 2019-2023 | 2016-2023 | both periods, separately |
| FOMC days | (not stated) | not skipped | not skipped in Part A; skipped in Parts B and C as on the rest of the bench |

## Part A: the paper's opening-range strategy on stocks in play

Pass-bar checks (our costs, normal entry-minute rule):

- at least 300 trades: yes
- avg R after costs > 0 in at least 4 of 5 research years: no
- avg R after costs > 0 over 2016-2018: no
- overall avg R after costs >= 3 SE above zero: no
- beats the opposite direction by >= 3 SE: yes

### Funnel

| Period | Selected stock-days | Flat first candle | No breakout | No bars | Trades | Long / short |
|---|---|---|---|---|---|---|
| 2016-2018 | 14800 | 155 | 2849 | 47 | 11749 | 5939 / 5810 |
| 2019-2023 | 25160 | 208 | 4439 | 30 | 20483 | 10227 / 10256 |
| 2016-2023 | 39960 | 363 | 7288 | 77 | 32232 | 16166 / 16066 |

### In R (R = the stop distance, 10% of the 14-day ATR)

| Period | Trades | Avg R before costs | Avg R, paper's cost ($0.0035/share) | Avg R after our costs | ± SE (by day) | z vs 0 | Strict entry-minute stop, our costs | vs opposite direction (R) | z | vs random direction (R) | z | Stopped out | Median R (% of price) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2016-2018 | 11749 | +0.364 | +0.296 | -0.231 | 0.044 | -5.3 | -0.817 | +0.340 | +6.2 | +0.190 | +5.1 | 84% | 0.27% |
| 2019-2023 | 20483 | +0.330 | +0.273 | -0.119 | 0.038 | -3.2 | -0.667 | +0.286 | +6.1 | +0.163 | +5.0 | 85% | 0.40% |
| 2016-2023 | 32232 | +0.343 | +0.281 | -0.160 | 0.029 | -5.5 | -0.722 | +0.306 | +8.6 | +0.173 | +7.0 | 85% | 0.34% |

### By year (R per trade)

| Year | Trades | Before costs | Paper's cost | Our costs | Our costs vs opposite (z) |
|---|---|---|---|---|---|
| 2016 | 3790 | +0.308 | +0.239 | -0.267 | +0.201 (+2.3) |
| 2017 | 3945 | +0.301 | +0.229 | -0.364 | +0.286 (+3.0) |
| 2018 | 4014 | +0.479 | +0.416 | -0.067 | +0.525 (+5.2) |
| 2019 | 4009 | +0.405 | +0.341 | -0.151 | +0.337 (+3.2) |
| 2020 | 4142 | +0.262 | +0.206 | -0.143 | +0.237 (+2.1) |
| 2021 | 4175 | +0.414 | +0.358 | -0.006 | +0.282 (+2.4) |
| 2022 | 4085 | +0.391 | +0.339 | +0.013 | +0.458 (+4.9) |
| 2023 | 4072 | +0.180 | +0.120 | -0.313 | +0.118 (+1.3) |

### As an account ($25,000 start; 1% of opening equity at risk per trade; open positions capped at 4× equity)

| Period | Costs | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | Total | Worst peak-to-trough | Trades taken |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2016-2018 | before costs | +2,286% | +161% | +4,951% |  |  |  |  |  | ×3.14e+03 | -60% | 5266 |
| 2016-2018 | paper's ($0.0035/share) | +1,198% | +37% | +2,547% |  |  |  |  |  | ×472 | -64% | 5244 |
| 2016-2018 | ours | -79% | -99% | -53% |  |  |  |  |  | -100% | -100% | 4983 |
| 2019-2023 | before costs |  |  |  | +17,343% | +1,475% | +22,550% | +53,956% | +572% | ×2.26e+09 | -71% | 11154 |
| 2019-2023 | paper's ($0.0035/share) |  |  |  | +9,186% | +559% | +9,742% | +25,999% | +221% | ×5.05e+07 | -75% | 11115 |
| 2019-2023 | ours |  |  |  | +4% | -95% | -20% | +259% | -98% | -100% | -100% | 11083 |

## Part B: the two T11 leads on 2016-2018 (T11 definitions, control on another day)

| Lead | Measure | all9 count | all9 result | all9 z | all9 by year (2016 / 2017 / 2018) | spy count | spy result | Verdict |
|---|---|---|---|---|---|---|---|---|
| kc_mom_p6_m2 long, 5-min | share our way at 10 and 30 min vs control taken long | 2742 | 10 min: 52.2% vs 48.8% (+3.4 pts) ; 30 min: 53.9% vs 48.5% (+5.4 pts) | +2.1 / +3.1 | 10 min: +7.3 / +0.1 / +2.7 ; 30 min: +6.0 / +4.5 / +5.8 | 300 | 10 min: +8.7 pts (z +2.1) ; 30 min: +6.3 pts (z +1.5) | FAIL |
| box_k0.25_c0 long, 5-min | race to 1.0x box height: expectancy vs control | 4411 | +0.057% vs +0.021% per race (gap +0.036%) | +3.7 | +0.023 / +0.027 / +0.055 | 303 | gap +0.013% (z +0.9) | PASS |
| box_k0.25_c0 short, 5-min | race to 1.0x box height: expectancy vs control | 4165 | +0.056% vs +0.023% per race (gap +0.033%) | +2.7 | +0.016 / +0.030 / +0.051 | 315 | gap +0.019% (z +1.2) | FAIL |
| box_k0.25_c1 long, 5-min | race to 1.0x box height: expectancy vs control | 3020 | +0.070% vs +0.017% per race (gap +0.053%) | +4.6 | +0.047 / +0.041 / +0.067 | 202 | gap +0.004% (z +0.2) | PASS |
| box_k0.25_c1 short, 5-min | race to 1.0x box height: expectancy vs control | 2650 | +0.083% vs +0.024% per race (gap +0.059%) | +4.3 | +0.042 / +0.059 / +0.074 | 199 | gap +0.037% (z +2.0) | PASS |

## Part C: big-gap sip_orb on 2016-2018 (T12 universe and rule)

| Gap | Bars | Trades | Avg R after costs (2R trade) | ± SE | z vs 0 | 2016 / 2017 / 2018 | Before costs | 1R trade | 3R trade | Hit +2R | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ≥ 8% | 5-min | 765 | +0.046 | 0.036 | +1.3 | +0.079 / +0.067 / +0.002 | +0.109 | +0.018 | +0.061 | 10% | FAIL |
| ≥ 8% | 2-min | 614 | +0.054 | 0.046 | +1.2 | +0.124 / +0.061 / -0.009 | +0.118 | -0.001 | +0.058 | 14% | FAIL |
| ≥ 8% | both (reference) | 1379 | +0.050 | 0.038 | +1.3 | +0.099 / +0.064 / -0.003 | +0.113 | +0.010 | +0.059 | 11% |  |
| ≥ 15% | 5-min | 217 | -0.007 | 0.067 | -0.1 | +0.065 / -0.005 / -0.066 | +0.045 | -0.013 | +0.011 | 6% | FAIL |
| ≥ 15% | 2-min | 171 | +0.025 | 0.089 | +0.3 | +0.129 / +0.009 / -0.050 | +0.083 | -0.039 | +0.044 | 14% | FAIL |
| ≥ 15% | both (reference) | 388 | +0.007 | 0.073 | +0.1 | +0.094 / +0.001 / -0.059 | +0.062 | -0.024 | +0.025 | 10% |  |

## Method

Part A, the paper's "stocks in play" 5-minute opening range (Zarattini, Barbon and Aziz 2024), on the top 20 by relative volume (t13_data): direction from the first 5-minute candle (9:30-9:35; up -> long only, down -> short only, flat -> no trade); entry when a 1-minute bar from 9:35 on trades through the candle's high (long) or low (short), filled at that level, or at the minute's open if it opens beyond; stop 10% of the 14-day ATR from the fill; exit at the stop (at the stop price, or the minute's open if it opens through) or at the close of the last regular-session minute (15:59). On the entry minute itself only a close beyond the stop counts as stopped (the bar's low may come before the fill); the "strict" version counts any touch on the entry minute. R = the stop distance. Costs per side: ours 0.05% of price + $0.01 per share; the paper's $0.0035 per share. Account: $25,000 start, each trade sized to lose 1% of the day's opening equity at the stop, total open positions capped at 4x that equity (a trade gets what is left of the cap, or nothing). FOMC days are not skipped here (the paper does not skip them). Controls: the same stock, entry moment and R, the opposite direction; and a random direction (seed 7).

Part B, the two T11 leads on 2016-2018 with T11's own code and its T10b-style control (another day of the same year, same time +-5 minutes); FOMC days skipped. Part C, T12's universe and sip_orb on 2016-2018 (t12.run), for gaps of at least 8% and at least 15%.
