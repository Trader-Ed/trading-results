T18 OUTCOME: NOT TRADEABLE

# T18: cost test in shares of kc_mom_p6_m2 long (5-minute bars), measured NBBO costs

Run 2026-10-29. Pass bar fixed in advance; holdout untouched; rulebook.yaml unchanged.

## Findings

- The pass bar fails on 2 of 3 checks. On 2019-2023 the 30-minute trade makes +0.051% per trade after measured costs, but that is only 2.5 standard errors above zero; the bar needs 3. On 2016-2018 it loses -0.007% per trade. Only the "4 of 5 years" check is met (2023 is negative).
- Costs take about 0.03-0.04% per trade on average. Most of that comes from the wider-spread stocks: GOOGL, TSLA, AMZN and NVDA have average entry spreads of 0.05-0.07%, which wipes out their edge. AAPL is the exception (+0.097% per trade after costs). SPY and QQQ spreads are tiny (0.004-0.006%), but their moves are small too. SPY alone is positive in both periods (+0.027%, z +1.6; and +0.033%, z +2.9), but SPY is not the pass universe and has only about 330 and 205 trades.
- The 60-minute exit (for information only) reaches z +3.0 on 2019-2023 and is positive in 5 of 5 years. On 2016-2018 it is flat (-0.003%), so it would not pass either. It was not chosen in advance, so it does not count.
- Account view: $2,500 grows to about $4,990 over 2019-2023, but most of the gain comes from 2022. 2023 is -4.4%, and 2016-2018 ends at $2,323. The worst drops are -12.6% and -15.1%. Per trade this is under $1 on $1,100 positions, so even a small amount of extra slippage beyond the quoted NBBO would erase it.
- Verdict: NOT TRADEABLE in shares as tested. Nothing goes to the holdout.

## Pass bar (30-minute exit, all nine stocks)

| Check | Result | Met |
|---|---|---|
| 2019-2023: avg return after costs >= 3 SE above zero | +0.051% per trade, z +2.5 | no |
| 2019-2023: positive in at least 4 of 5 years | 4 of 5 | yes |
| 2016-2018: positive | -0.007% per trade | no |

## Results by exit, period and universe

| Exit | Period | Universe | Trades | Avg return after costs | SE | z | Mid-to-mid move (no costs) | Avg spread at entry | Winners | Years positive |
|---|---|---|---|---|---|---|---|---|---|---|
| 30 min | 2019-2023 | all9 | 3,227 | +0.051% | 0.021% | +2.5 | +0.084% | 0.034% | 53.5% | 4 of 5 |
| 30 min | 2019-2023 | SPY | 333 | +0.027% | 0.016% | +1.6 | +0.032% | 0.003% | 53.5% | 4 of 5 |
| 30 min | 2016-2018 | all9 | 2,038 | -0.007% | 0.019% | -0.4 | +0.030% | 0.039% | 51.1% | 1 of 3 |
| 30 min | 2016-2018 | SPY | 205 | +0.033% | 0.011% | +2.9 | +0.039% | 0.004% | 58.0% | 3 of 3 |
| 60 min (info only) | 2019-2023 | all9 | 3,195 | +0.079% | 0.026% | +3.0 | +0.110% | 0.034% | 54.1% | 5 of 5 |
| 60 min (info only) | 2019-2023 | SPY | 333 | +0.039% | 0.020% | +1.9 | +0.044% | 0.003% | 60.4% | 4 of 5 |
| 60 min (info only) | 2016-2018 | all9 | 2,013 | -0.003% | 0.024% | -0.1 | +0.032% | 0.039% | 52.1% | 1 of 3 |
| 60 min (info only) | 2016-2018 | SPY | 205 | +0.018% | 0.016% | +1.2 | +0.025% | 0.004% | 53.2% | 3 of 3 |

## By year (30-minute exit, all nine stocks)

| Year | Trades | Avg return after costs | Mid-to-mid move | Avg spread at entry | Avg spread at exit |
|---|---|---|---|---|---|
| 2016 | 682 | +0.025% | +0.064% | 0.042% | 0.032% |
| 2017 | 712 | -0.014% | +0.019% | 0.035% | 0.027% |
| 2018 | 644 | -0.031% | +0.007% | 0.040% | 0.032% |
| 2019 | 796 | +0.051% | +0.083% | 0.035% | 0.026% |
| 2020 | 642 | +0.044% | +0.088% | 0.045% | 0.039% |
| 2021 | 682 | +0.057% | +0.091% | 0.037% | 0.028% |
| 2022 | 453 | +0.147% | +0.180% | 0.036% | 0.027% |
| 2023 | 654 | -0.012% | +0.005% | 0.019% | 0.014% |

## Measured spreads by stock (30-minute trades, both periods)

| Stock | Trades | Avg spread at entry | Median at entry | Avg spread at exit | Avg return after costs |
|---|---|---|---|---|---|
| AAPL | 550 | 0.013% | 0.011% | 0.010% | +0.097% |
| AMZN | 644 | 0.053% | 0.047% | 0.042% | -0.000% |
| GOOGL | 561 | 0.072% | 0.068% | 0.059% | +0.002% |
| META | 558 | 0.026% | 0.023% | 0.019% | +0.019% |
| MSFT | 518 | 0.014% | 0.014% | 0.012% | +0.021% |
| NVDA | 655 | 0.053% | 0.046% | 0.036% | +0.013% |
| QQQ | 596 | 0.006% | 0.006% | 0.006% | +0.046% |
| SPY | 538 | 0.004% | 0.004% | 0.004% | +0.029% |
| TSLA | 645 | 0.071% | 0.060% | 0.057% | +0.040% |

| Stock | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 |
|---|---|---|---|---|---|---|---|---|
| AAPL spread | 0.011% | 0.012% | 0.014% | 0.014% | 0.018% | 0.010% | 0.011% | 0.010% |
| AMZN spread | 0.064% | 0.053% | 0.060% | 0.049% | 0.062% | 0.068% | 0.057% | 0.017% |
| GOOGL spread | 0.078% | 0.067% | 0.078% | 0.071% | 0.098% | 0.087% | 0.087% | 0.016% |
| META spread | 0.016% | 0.016% | 0.023% | 0.029% | 0.026% | 0.031% | 0.034% | 0.034% |
| MSFT spread | 0.018% | 0.013% | 0.012% | 0.011% | 0.015% | 0.014% | 0.017% | 0.016% |
| NVDA spread | 0.051% | 0.053% | 0.063% | 0.061% | 0.058% | 0.055% | 0.040% | 0.040% |
| QQQ spread | 0.009% | 0.007% | 0.007% | 0.006% | 0.006% | 0.004% | 0.007% | 0.004% |
| SPY spread | 0.005% | 0.004% | 0.004% | 0.004% | 0.004% | 0.003% | 0.003% | 0.003% |
| TSLA spread | 0.108% | 0.080% | 0.090% | 0.076% | 0.085% | 0.048% | 0.055% | 0.023% |

## Account view ($2,500, $10,000 intraday buying power, 30-minute exit)

Each trade is sized at one ninth of the buying power (4x the day's opening equity), so every signal is taken; profits and losses compound daily.

| Period | Start $/trade | Avg $ per trade | Trades per day (trading days with a trade) | Max open at once | Yearly return | Worst day | Worst month | Largest peak-to-trough drop | End equity |
|---|---|---|---|---|---|---|---|---|---|
| 2019-2023 | $1,111 | +$0.77 | 3.68 | 9 | 2019: +18.8%, 2020: +12.0%, 2021: +18.2%, 2022: +32.9%, 2023: -4.4% | -7.9% (2020-03-25) | -9.1% (2020-03) | -12.6% | $4,992 |
| 2016-2018 | $1,111 | -$0.09 | 3.51 | 9 | 2016: +7.2%, 2017: -4.8%, 2018: -9.0% | -2.8% (2016-02-12) | -5.5% (2018-12) | -15.1% | $2,323 |

## Data

Signals before the one-position filter: 7,090. Trades: 30-minute exit 5,265, 60-minute exit 5,208. No valid quote found: none. Trades needing the 2-minute fallback window: 17. Median wait from the bar's close to the first quote: 15 ms.

## Method

Signals: exactly T11's rule as saved (reports/bench/signals_t11 for 2019-2023, T13 Part B's re-run for
2016-2018): a 5-minute bar closing above its 6-bar Keltner band (6-bar average of the typical price + 2x the
6-bar ATR), decided 9:35-11:50, FOMC days skipped, all nine stocks. One position per stock at a time: a
signal is skipped while that stock's position is open (from the entry moment until its exit moment).
Entry: buy at the NBBO ask of the first valid quote at or after the signal bar's close (the decision minute,
hh:mm:00). Exit: sell at the NBBO bid in force exactly 30 minutes later (the last valid quote at or before
hh:mm:00 + 30 minutes); 60 minutes as a secondary, for information only, with its own one-position filter.
A valid quote has bid > 0, ask > 0 and ask >= bid. Costs: no commission; the SEC and FINRA sale fees (T14's
tables). Return per trade = (exit bid - entry ask - fees per share) / entry ask. Quotes are downloaded only
for a few seconds after each entry moment and before each exit moment (more only if none is found).
Account: $2,500, intraday buying power 4x the day's opening equity ($10,000 at the start); every trade is
sized at one ninth of that buying power, so all nine stocks can be held at once and no signal is skipped.
