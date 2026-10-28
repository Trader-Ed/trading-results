MEASUREMENT OUTCOME: NO CANDIDATE

# T14: measuring T13 Part A with trades and quotes (2016-2023)

**Comparisons judged: 3 stop widths**, each against five fixed checks. Holdout (2024-2025) not used.

## Findings

**No stop width passes, so nothing goes to the 2024-2025 holdout.** On the tick sample, after measured costs, every width is a little positive, but none is 3 standard errors above zero. On the full bar set under the strict entry-minute rule, every width is negative.

### Step 1, sample
4,000 T13 Part A trades (500 a year, 250 long and 250 short, seed fixed). 3,981 were replayed from ticks: for 18 there was no valid NBBO quote just before the fill, and for 1 no counted trade at the breakout level. 4 stops (wider widths) touched on a 1-minute bar but never on a counted trade, so those trades exit at the close.

### Step 2, what the ticks show
- **The entry minute was the big unknown in T13.** At the paper's 10% stop, the stop was touched inside the entry minute before the fill in 42.7% of trades, and after the fill (a real stop-out) in 21.9%. In 30.2% the only touch came before the fill, and T13's strict rule wrongly counted all of those as stopped. At 25% of ATR the shares are 10.1% / 4.6%; at 50%, 1.4% / 0.8%.
- **Spread at the fill:** 0.16-0.28% of price by year (widest in 2020-2022), and 0.16% ($100+) to 0.46% ($5-10) by price band. In R it is about 0.4R at the 10% stop, 0.15R at 25% and 0.08R at 50%.
- **Entry slippage vs the breakout level** (buying at the ask): mean 0.03-0.06% of price, median near 0. **Stop slippage vs the stop** (selling at the bid): mean 0.03-0.11%, rising over the years; 0.13% for $5-10 stocks and 0.05% for $50+.
- **Fees** (SEC and FINRA on sales; $0 commission) cost 0.007R at the 10% stop and less at wider stops.

### Step 3, results (average R per trade after measured costs)
- **Tick sample:** +0.076R at 10% of ATR (z +1.0, 6 of 8 years positive), +0.099R at 25% (z +2.5, 7 of 8), +0.069R at 50% (z +2.9, 6 of 8). Before costs: +0.08, +0.10, +0.07R.
- **Bar set (32,232 trades, calibrated costs):** under the strict rule, -0.545R, -0.108R and -0.014R (no year above zero by 3 SE). Under the close rule, +0.034R, -0.001R and -0.001R.
- **Which bar rule matches the ticks:** on the same sampled trades, the close rule gives +0.095R and +0.058R at 25% and 50%, against +0.099R and +0.069R from ticks: a close match. At 10% it is too generous (+0.20R against +0.08R). The strict rule is too harsh at 10% and 25%.
- **So the most likely full-set result is about zero after costs at 25% and 50%** (the close rule over all 32,232 trades), and slightly positive at best at 10%. The sample's +0.07 to +0.10R is likely partly sample luck: it is about 2.5 sample standard errors above the full-set figure.
- **Direction is real but doesn't pay.** In every version, trading the first candle's direction beats the opposite direction by 3 SE or more (z +7 to +14). The opposite side loses heavily at the breakout moment, but the strategy's own side only breaks even after costs.

### Step 4, pass bar
Every width fails on the tick sample (z below 3) and on the bar set's strict rule (negative). The bar-set test can be read two ways: z ≥ 3 in each of at least 6 years, or z ≥ 3 overall with at least 6 years positive. Both fail. Only the opposite-direction checks pass.

### Step 5, practical checks (read-only)
- **Buying power:** the paper account has $2,500 equity, multiplier 4, buying power $10,000 and Reg T overnight buying power $5,000. It reports no day-trading buying power or pattern-day-trader field. Alpaca's documentation says FINRA's intraday margin rule has replaced the pattern-day-trader rule (no $25,000 minimum, unlimited day trades, $2,000 minimum equity for margin).
- **Position sizes fit:** at 1% risk ($25), the median position is about $7,560 at the 10% stop, $3,020 at 25% and $1,510 at 50%, all within $10,000. At the 10% stop only one position at a time fits.
- **Borrow:** 86% of the sample's shorts, and 87% of all T13 shorts, are in stocks Alpaca marks easy to borrow today. 7% of those symbols are no longer listed as active. Historical borrow status is not available.
- **No account simulation was run,** because no width passed.

### Notes
- **Fee rates:** SEC Section 31 rates by date are partly approximate (confirmed: $13.00 per million to 2019-04-15, $22.90 → $8.00 on 2023-02-27); FINRA TAF $0.000119 a share to 2021, then $0.000130 and $0.000145. Either fee is under 0.003% of a sale.
- **Data:** 4,000 entry windows and 10,962 stop windows of trades and NBBO quotes were downloaded, about 2.4 hours at Alpaca's rate limit. Nothing was run on 2024-2025.

## Pass bar by stop width

| Stop width | Tick sample: avg R (measured costs) | z | Years > 0 | vs opposite (z) | Bar set, strict: avg R | z | Years > 0 with z ≥ 3 | Years > 0 | vs opposite (z) | Verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| 10% of ATR | +0.076 | +1.0 | 6/8 | +0.780 (+9.0) | -0.545 | -29.0 | 0/8 | 0/8 | +0.219 (+9.7) | FAIL |
| 25% of ATR | +0.099 | +2.5 | 7/8 | +0.432 (+8.2) | -0.108 | -8.4 | 0/8 | 0/8 | +0.236 (+13.5) | FAIL |
| 50% of ATR | +0.069 | +2.9 | 6/8 | +0.263 (+7.2) | -0.014 | -1.6 | 0/8 | 3/8 | +0.163 (+12.3) | FAIL |

## By year (avg R after costs)

| Year | Tick 10% | Tick 25% | Tick 50% | Bars strict 10% | Bars strict 25% | Bars strict 50% | Bars close-rule 10% | Bars close-rule 25% | Bars close-rule 50% |
|---|---|---|---|---|---|---|---|---|---|
| 2016 | +0.235 | +0.199 | +0.089 | -0.549 | -0.092 | -0.031 | -0.036 | -0.008 | -0.015 |
| 2017 | +0.023 | +0.068 | +0.022 | -0.754 | -0.224 | -0.059 | -0.119 | -0.070 | -0.036 |
| 2018 | +0.124 | +0.122 | +0.115 | -0.562 | -0.072 | +0.018 | +0.137 | +0.061 | +0.035 |
| 2019 | +0.311 | +0.268 | +0.129 | -0.625 | -0.106 | -0.004 | +0.051 | +0.015 | +0.010 |
| 2020 | -0.094 | -0.056 | -0.045 | -0.456 | -0.117 | -0.034 | -0.002 | -0.043 | -0.028 |
| 2021 | +0.062 | +0.122 | +0.113 | -0.503 | -0.057 | +0.023 | +0.169 | +0.077 | +0.035 |
| 2022 | +0.200 | +0.055 | +0.144 | -0.370 | -0.037 | +0.000 | +0.176 | +0.022 | +0.010 |
| 2023 | -0.254 | +0.017 | -0.018 | -0.556 | -0.164 | -0.029 | -0.118 | -0.062 | -0.021 |

## Tick sample: results by stop width

| Stop width | Trades | Before costs (R) | After measured costs (R) | Fees (R) | Stopped | Opposite direction after costs (R) | Bar set, close rule (R) | z | Bar set, strict (R) | z |
|---|---|---|---|---|---|---|---|---|---|---|
| 10% | 3981 | +0.083 | +0.076 | 0.0068 | 86% | -0.704 | +0.034 | +1.2 | -0.545 | -29.0 |
| 25% | 3981 | +0.102 | +0.099 | 0.0027 | 68% | -0.333 | -0.001 | -0.0 | -0.108 | -8.4 |
| 50% | 3981 | +0.070 | +0.069 | 0.0014 | 44% | -0.194 | -0.001 | -0.1 | -0.014 | -1.6 |

## Entry minute: stop touched before or after the fill

| Stop width | Touched in the entry minute before the fill | After the fill (the trade is stopped there) | Touched only before |
|---|---|---|---|
| 10% | 42.7% | 21.9% | 30.2% |
| 25% | 10.1% | 4.6% | 8.8% |
| 50% | 1.4% | 0.8% | 1.3% |

Fills after the entry minute (the first counted trade at the level came later than the bar suggests): 0.0%.

## Spread and slippage by year

| Year | Trades | Spread at fill (% of price) | Spread in R at 10% / 25% / 50% ATR | Entry slippage vs the level (% of price): mean / median | Stop slippage vs the stop (% of price): mean / median (stops) |
|---|---|---|---|---|---|
| 2016 | 500 | 0.167% | 0.39 / 0.16 / 0.08 | 0.034% / 0.008% | 0.033% / 0.028% (938) |
| 2017 | 500 | 0.158% | 0.44 / 0.17 / 0.09 | 0.033% / 0.000% | 0.048% / 0.030% (983) |
| 2018 | 497 | 0.177% | 0.39 / 0.16 / 0.08 | 0.041% / 0.000% | 0.070% / 0.034% (1003) |
| 2019 | 499 | 0.197% | 0.41 / 0.16 / 0.08 | 0.041% / 0.011% | 0.062% / 0.035% (977) |
| 2020 | 496 | 0.263% | 0.38 / 0.15 / 0.08 | 0.053% / 0.009% | 0.083% / 0.046% (1008) |
| 2021 | 498 | 0.256% | 0.37 / 0.15 / 0.07 | 0.037% / 0.003% | 0.073% / 0.043% (1023) |
| 2022 | 495 | 0.279% | 0.37 / 0.15 / 0.07 | 0.058% / 0.019% | 0.090% / 0.054% (931) |
| 2023 | 496 | 0.216% | 0.37 / 0.15 / 0.07 | 0.056% / 0.015% | 0.112% / 0.041% (1024) |

## Spread and slippage by price band

| Band | Trades | Spread at fill (% of price) | Spread in R at 10% / 25% / 50% ATR | Entry slippage vs the level (% of price): mean / median | Stop slippage vs the stop (% of price): mean / median (stops) |
|---|---|---|---|---|---|
| $5-10 | 212 | 0.464% | 0.31 / 0.12 / 0.06 | 0.071% / 0.000% | 0.128% / 0.099% (402) |
| $10-20 | 612 | 0.273% | 0.29 / 0.11 / 0.06 | 0.045% / 0.000% | 0.117% / 0.054% (1165) |
| $20-50 | 1621 | 0.209% | 0.38 / 0.15 / 0.08 | 0.050% / 0.008% | 0.072% / 0.037% (3214) |
| $50-100 | 935 | 0.164% | 0.46 / 0.19 / 0.09 | 0.036% / 0.014% | 0.048% / 0.029% (1884) |
| $100+ | 601 | 0.157% | 0.44 / 0.18 / 0.09 | 0.030% / 0.010% | 0.047% / 0.030% (1222) |

## Cost model for the bar set (means from the tick sample, % of price)

| Price band | Sample trades | Entry slippage | Control entry slippage | Stop slippage | Control stop slippage | Spread |
|---|---|---|---|---|---|---|
| $5-10 | 212 | 0.071% | 0.394% | 0.128% | 0.130% | 0.464% |
| $10-20 | 612 | 0.045% | 0.228% | 0.117% | 0.093% | 0.273% |
| $20-50 | 1621 | 0.050% | 0.159% | 0.072% | 0.069% | 0.209% |
| $50-100 | 935 | 0.036% | 0.128% | 0.048% | 0.050% | 0.164% |
| $100+ | 601 | 0.030% | 0.127% | 0.047% | 0.044% | 0.157% |

## Practical checks (read-only, paper account and asset list, 2026-10-28)

- Paper account: equity $2,500; multiplier 4; buying power $10,000; Reg T (overnight) buying power $5,000; day-trading buying power field: not reported; pattern-day-trader flag: not reported.
- Position size at 1% risk on $2,500 ($25 at risk), median over the tick sample: 10% ATR stop: $7,559; 25% ATR stop: $3,024; 50% ATR stop: $1,512 of stock, against $10,000 of intraday buying power.
- Short trades in stocks Alpaca marks easy to borrow today: 86% of the sample's shorts (1992), 87% of all T13 shorts (16066); 7% of those symbols are no longer active on Alpaca. Historical borrow status is not available.

## Method

Tick replay. Trades that count are those that set the last sale: odd lots and out-of-sequence, average-price, derivatively priced, extended-hours, cash, next-day, seller's-option, bunched-sold, market-center open/close and prior-reference prints are left out (conditions B C G H I M N P Q R T U V W Z 4 7 9). Fill: the first such trade at or beyond the breakout level (the 9:30-9:35 high for longs, low for shorts, from 1-minute bars) from 9:35:00 on; the buy fills at the NBBO ask at that moment (the latest quote at or before the trade; the sell at the bid). Stop: the stop level is set from the actual fill; the first counted trade at or beyond it after the fill exits at the NBBO bid (ask for shorts). Otherwise the exit is the official closing price (Alpaca's daily close). Costs: $0 commission, plus on every sale the SEC Section 31 fee and FINRA's trading activity fee. The opposite-direction control enters at the same moment on the other side of the quote (sells at the bid for a long signal), with the same R, and is replayed the same way.

Bar set: every T13 Part A trade, replayed on 1-minute bars with costs calibrated from the tick sample by price band (mean entry slippage vs the breakout level, mean stop slippage vs the stop, both as % of price, for the signal and the control separately), the official close, and the same fees. Both entry-minute rules: "close" (the entry minute counts as stopped only if it closes beyond the stop) and "strict" (any touch).

---

Full per-trade tables: [history/2026-10-28-t14-measurement.md](history/2026-10-28-t14-measurement.md)
