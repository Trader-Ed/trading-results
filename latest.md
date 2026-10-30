BENCH CHECK: OK (2026-10-30 06:31, code c0b9593 + uncommitted changes, fingerprint 3cfbef1b36db)

T20 OUTCOME — V: NO PASS; M: NO PASS

# T20: "Whales", fading the prior two days' highs and lows (ProRealAlgos video)

Run 2026-10-30. Pass bar fixed in advance by the partners; 2024-2025 holdout untouched; rulebook.yaml unchanged. Data 2016-2023, the nine bench stocks (all9), SPY also alone.

## Findings

- Neither version passes. Both lose about 1 R per trade after costs (V -1.03 R, z -6.2, 13,030 trades; M -1.04 R, z -5.0, 9,988 trades), and both are negative in all 8 years. SPY alone is negative too (V -0.18 R, M -0.12 R).
- Before costs the fade is break-even: -0.05 R per trade in both versions. Prior-day highs and lows, faded at the first touch, show no edge here. The opposite trade (buying the breakout) does better before costs (V +0.31 R, M +0.67 R) and beats the fade by 3.3 SE in V. But it also loses after costs (V -0.66 R, M -0.24 R), so it is not a lead either.
- The rules make the stops very tight: the stop is 0.1% beyond the outer level, and the entry can already be up to 0.1% past the level. The median stop is about 0.4% of price, and 1 trade in 10 has a stop under 0.05%. On those trades the spread alone costs several R (-8 to -9 R per trade on average after costs). Leaving them out does not rescue the test: the rest still lose -0.24 to -0.27 R (z -10 to -12).
- Targets are rarely reached: 951 of 13,030 V trades and 355 of 9,988 M trades. Most trades end at the stop (V 55%, M 47%) or at the time exit.
- By half-hour (information only) no time of day is positive after costs in either version. The 9:30-10:00 half-hour holds half or more of all trades (V 54%, M 64%).
- Account view: both versions lose almost the whole $2,500 (V ends at $26, M at $41; largest drop about -99%). Once equity is that small, 1% risk usually buys less than one share, so most later signals are not taken.
- Calendars for M: FOMC days from config.yaml. GDP days: all 95 BEA releases for 2016-2023 (advance, second and third estimates), from bea.gov's news archive. Jobs and CPI days are NOT applied: bls.gov refuses automated access, FRED and FRASER could not be reached from this machine, and no other official source was available. Earnings: Alpha Vantage's historical report dates (224 reports for the 7 stocks; ETFs have none). Alpha Vantage marks every report after the close except three of Microsoft's July reports (2021-2023), which it marks before the open. Microsoft released those after the close too, so for every report both the report day and the next session are skipped. That can only remove trades, never add them.
- Costs: the spread is T18's measured average quoted spread per stock and year, paid in full at entry and again on stop exits. Paying it on time exits as well would lower the averages by up to about 0.04 R more (shown under the summary).

## Pass bar, V (video): NO PASS

| Check | Result | Met |
|---|---|---|
| at least 300 trades | 13,030 | yes |
| avg R after costs >= 3 SE above zero (clustered by day) | -1.031 R, z -6.2 | no |
| positive in at least 6 of 8 years | 0 of 8 | no |
| beats the opposite trade by >= 3 SE | -0.374 R per trade, z -3.3 | no |
| SPY alone points the same way (avg R after costs > 0) | -0.182 R on 1,627 trades | no |

## Pass bar, M (machine-style): NO PASS

| Check | Result | Met |
|---|---|---|
| at least 300 trades | 9,988 | yes |
| avg R after costs >= 3 SE above zero (clustered by day) | -1.041 R, z -5.0 | no |
| positive in at least 6 of 8 years | 0 of 8 | no |
| beats the opposite trade by >= 3 SE | -0.806 R per trade, z -1.6 | no |
| SPY alone points the same way (avg R after costs > 0) | -0.121 R on 1,222 trades | no |

## Summary

| Version | Universe | Trades | Win rate | Avg win R | Avg loss R | Avg R before costs | Avg R after costs | SE | z | Median R | Opposite trade avg R before costs | Opposite trade avg R after costs | Trade minus opposite (z) | Random direction avg R | Years positive |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M (machine-style) | all9 | 9,988 | 33.4% | +1.56 | -2.35 | -0.047 | -1.041 | 0.210 | -5.0 | -0.57 | +0.674 | -0.235 | -0.806 (-1.6) | -0.386 | 0 of 8 |
| M (machine-style) | SPY | 1,222 | 37.0% | +1.26 | -0.93 | -0.007 | -0.121 | 0.056 | -2.2 | -0.34 | +0.313 | +0.201 | -0.322 (-1.5) | +0.080 | 1 of 8 |
| V (video) | all9 | 13,030 | 30.2% | +1.94 | -2.32 | -0.054 | -1.031 | 0.167 | -6.2 | -1.04 | +0.312 | -0.657 | -0.374 (-3.3) | -0.775 | 0 of 8 |
| V (video) | SPY | 1,627 | 33.3% | +1.56 | -1.05 | -0.049 | -0.182 | 0.051 | -3.6 | -1.01 | +0.281 | +0.150 | -0.332 (-1.8) | +0.152 | 1 of 8 |

Avg R after costs if the spread were also paid on time exits (information only): M (machine-style) all9 -1.075; M (machine-style) SPY -0.129; V (video) all9 -1.053; V (video) SPY -0.187.

## By year (avg R after costs, trades in brackets)

| Version | Universe | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 |
|---|---|---|---|---|---|---|---|---|---|
| M (machine-style) | all9 | -2.234 (1380) | -0.900 (1454) | -0.692 (1209) | -0.820 (1222) | -0.596 (1099) | -1.277 (1269) | -0.660 (1133) | -0.934 (1222) |
| M (machine-style) | SPY | -0.008 (166) | -0.053 (181) | -0.332 (147) | -0.268 (139) | -0.122 (132) | -0.071 (155) | +0.095 (151) | -0.251 (151) |
| V (video) | all9 | -2.060 (1758) | -0.765 (1818) | -0.871 (1603) | -0.733 (1571) | -0.718 (1482) | -1.440 (1669) | -0.643 (1522) | -0.891 (1607) |
| V (video) | SPY | +0.028 (223) | -0.020 (220) | -0.590 (199) | -0.241 (180) | -0.181 (181) | -0.093 (207) | -0.092 (213) | -0.324 (204) |

## M (machine-style): by stock

| Stock | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| AAPL | 1,111 | 31.7% | +0.260 | -0.145 | -0.6 | -0.040 |
| AMZN | 1,087 | 30.5% | -0.160 | -1.548 | -4.9 | -1.290 |
| GOOGL | 1,182 | 30.1% | -0.290 | -3.084 | -1.9 | +1.297 |
| META | 1,138 | 32.7% | +0.008 | -1.234 | -1.9 | -1.281 |
| MSFT | 1,227 | 35.2% | -0.003 | -0.393 | -4.8 | +0.123 |
| NVDA | 934 | 32.9% | -0.120 | -1.490 | -3.8 | -1.314 |
| QQQ | 1,279 | 35.3% | +0.019 | -0.293 | -1.6 | -0.111 |
| SPY | 1,222 | 37.0% | -0.007 | -0.121 | -2.2 | +0.201 |
| TSLA | 808 | 34.5% | -0.186 | -1.368 | -7.8 | -0.003 |

## M (machine-style): by level

| Level | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| box 1 bottom | 2,526 | 34.1% | +0.008 | -0.737 | -7.7 | -0.637 |
| box 1 top | 3,100 | 28.5% | +0.062 | -0.944 | -7.8 | -0.793 |
| box 2 bottom | 2,007 | 39.2% | -0.155 | -1.538 | -1.6 | +1.262 |
| box 2 top | 2,355 | 34.1% | -0.157 | -1.070 | -3.3 | -0.345 |

## M (machine-style): by side

| Side | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| long (at a bottom) | 4,533 | 36.4% | -0.064 | -1.092 | -2.6 | +0.204 |
| short (at a top) | 5,455 | 30.9% | -0.033 | -0.998 | -6.5 | -0.600 |

## M (machine-style): by exit reason

| Exit | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| stop | 4,708 | 0.0% | -1.163 | -3.189 | -7.2 | +0.012 |
| target | 355 | 100.0% | +2.570 | +2.502 | +16.0 | -1.042 |
| time | 4,925 | 60.5% | +0.831 | +0.757 | +11.0 | -0.413 |

## M (machine-style): by time of entry (half-hour of the signal bar's close; information only)

| Half-hour | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| 09:30-10:00 | 6,363 | 31.5% | -0.053 | -1.173 | -3.6 | +0.014 |
| 10:00-10:30 | 1,689 | 38.0% | -0.043 | -0.849 | -4.4 | -0.775 |
| 10:30-11:00 | 958 | 33.6% | -0.083 | -0.562 | -8.0 | -0.281 |
| 11:00-11:30 | 677 | 36.6% | +0.072 | -0.875 | -3.7 | -0.806 |
| 11:30-12:00 | 301 | 38.9% | -0.099 | -1.214 | -3.4 | -1.047 |

## V (video): by stock

| Stock | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| AAPL | 1,444 | 28.9% | +0.224 | -0.181 | -0.7 | -0.000 |
| AMZN | 1,409 | 30.0% | -0.179 | -1.511 | -6.1 | -1.277 |
| GOOGL | 1,540 | 27.8% | -0.244 | -2.865 | -2.3 | -2.066 |
| META | 1,471 | 28.6% | -0.003 | -1.233 | -2.5 | -1.255 |
| MSFT | 1,560 | 30.9% | -0.008 | -0.574 | -3.8 | -0.233 |
| NVDA | 1,263 | 28.7% | -0.071 | -1.300 | -4.1 | -0.957 |
| QQQ | 1,608 | 32.6% | -0.001 | -0.291 | -1.9 | -0.138 |
| SPY | 1,627 | 33.3% | -0.049 | -0.182 | -3.6 | +0.150 |
| TSLA | 1,108 | 30.1% | -0.188 | -1.372 | -9.1 | -0.170 |

## V (video): by level

| Level | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| box 1 bottom | 3,290 | 30.5% | -0.000 | -0.810 | -8.1 | -0.487 |
| box 1 top | 4,009 | 25.2% | -0.016 | -1.042 | -6.9 | -0.803 |
| box 2 bottom | 2,659 | 34.5% | -0.139 | -1.374 | -1.9 | -0.933 |
| box 2 top | 3,072 | 32.5% | -0.086 | -0.958 | -3.8 | -0.411 |

## V (video): by side

| Side | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| long (at a bottom) | 5,949 | 32.3% | -0.062 | -1.062 | -3.3 | -0.687 |
| short (at a top) | 7,081 | 28.4% | -0.047 | -1.006 | -7.2 | -0.633 |

## V (video): by exit reason

| Exit | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| stop | 7,217 | 0.0% | -1.120 | -2.832 | -9.7 | -0.765 |
| target | 951 | 100.0% | +3.555 | +3.471 | +8.4 | -1.075 |
| time | 4,862 | 61.3% | +0.824 | +0.761 | +16.7 | -0.417 |

## V (video): by time of entry (half-hour of the signal bar's close; information only)

| Half-hour | Trades | Win rate | Avg R before costs | Avg R after costs | z | Opposite trade avg R |
|---|---|---|---|---|---|---|
| 09:30-10:00 | 6,981 | 29.8% | -0.045 | -1.119 | -3.7 | -0.639 |
| 10:00-10:30 | 1,861 | 34.8% | +0.036 | -0.742 | -4.1 | -0.801 |
| 10:30-11:00 | 1,054 | 30.2% | -0.073 | -0.656 | -5.1 | -0.506 |
| 11:00-11:30 | 736 | 30.2% | -0.070 | -1.021 | -4.7 | -0.678 |
| 11:30-12:00 | 487 | 26.7% | -0.242 | -1.175 | -5.0 | -0.723 |
| 12:00-12:30 | 396 | 27.8% | -0.165 | -1.297 | -2.5 | -0.670 |
| 12:30-13:00 | 280 | 24.6% | -0.250 | -1.482 | -2.9 | -1.144 |
| 13:00-13:30 | 225 | 30.7% | +0.033 | -1.171 | -3.3 | -1.281 |
| 13:30-14:00 | 260 | 25.0% | -0.128 | -0.850 | -4.4 | -0.556 |
| 14:00-14:30 | 277 | 30.0% | -0.251 | -1.116 | -4.4 | -0.615 |
| 14:30-15:00 | 232 | 27.6% | -0.197 | -1.411 | -3.3 | +1.103 |
| 15:00-15:30 | 241 | 31.1% | +0.304 | -0.756 | -2.1 | -1.227 |

## Account view ($2,500 start, 1% risk per trade, buying power 4x the day's opening equity)

| Version | Trades taken | Not taken: buying power in use | Not taken: 1% risk buys under 1 share | Not taken: day stop | Days stopped at -20% | Yearly return | Largest drop (end-of-day equity) | End equity |
|---|---|---|---|---|---|---|---|---|
| V (video) | 3,513 | 2,977 | 6,540 | n/a | n/a | 2016: -82.5%, 2017: -25.9%, 2018: -69.5%, 2019: -51.9%, 2020: -7.1%, 2021: -4.2%, 2022: -34.2%, 2023: -7.3% | -99.0% (2016-01-06 to 2023-03-16) | $26 |
| M (machine-style) | 3,188 | 2,206 | 4,594 | 0 | 0 | 2016: -73.1%, 2017: -52.1%, 2018: -57.0%, 2019: -49.7%, 2020: -9.4%, 2021: -3.0%, 2022: -33.7%, 2023: +0.5% | -98.6% (2016-01-06 to 2023-07-06) | $41 |

## Stop size and costs

| Version | Median stop distance | Trades with stop under 0.05% of price | Their avg R after costs | The other trades: avg R after costs (z) | Avg cost in R | Median cost in R |
|---|---|---|---|---|---|---|
| M (machine-style) | 0.397% | 938 (9.4%) | -8.803 | -0.236 (-10.3) | 0.994 | 0.078 |
| V (video) | 0.372% | 1,304 (10.0%) | -7.913 | -0.266 (-12.4) | 0.978 | 0.088 |

## Setups not traded

| Version | Stock | Stock-days | No box | Skipped by M's calendar | Breakout days | Bars at a top and a bottom | Target not beyond entry |
|---|---|---|---|---|---|---|---|
| V (video) | AAPL | 2,012 | 2 | 0 | 1,218 | 53 | 0 |
| V (video) | AMZN | 2,012 | 2 | 0 | 1,257 | 36 | 0 |
| V (video) | NVDA | 2,012 | 2 | 0 | 1,257 | 25 | 0 |
| V (video) | MSFT | 2,012 | 2 | 0 | 1,190 | 17 | 0 |
| V (video) | META | 2,012 | 2 | 0 | 1,216 | 27 | 0 |
| V (video) | GOOGL | 2,012 | 2 | 0 | 1,220 | 47 | 0 |
| V (video) | TSLA | 2,012 | 2 | 0 | 1,275 | 5 | 0 |
| V (video) | SPY | 2,012 | 2 | 0 | 1,181 | 76 | 0 |
| V (video) | QQQ | 2,012 | 2 | 0 | 1,237 | 46 | 0 |
| M (machine-style) | AAPL | 2,012 | 2 | 196 | 918 | 18 | 0 |
| M (machine-style) | AMZN | 2,012 | 2 | 197 | 978 | 18 | 0 |
| M (machine-style) | NVDA | 2,012 | 2 | 214 | 963 | 20 | 0 |
| M (machine-style) | MSFT | 2,012 | 2 | 203 | 899 | 17 | 0 |
| M (machine-style) | META | 2,012 | 2 | 188 | 930 | 21 | 0 |
| M (machine-style) | GOOGL | 2,012 | 2 | 206 | 922 | 14 | 0 |
| M (machine-style) | TSLA | 2,012 | 2 | 206 | 990 | 4 | 0 |
| M (machine-style) | SPY | 2,012 | 2 | 156 | 858 | 54 | 0 |
| M (machine-style) | QQQ | 2,012 | 2 | 156 | 949 | 31 | 0 |

## Method

Data: the nine bench stocks (all9), 2016-2023, SPY also reported alone; holdout untouched. 5-minute bars built
from the bench's 1-minute bars (anchored at 9:30, decided at their close), converted to the day's actual prices
(Alpaca's daily raw close / adjusted close, as T15; SPY and QQQ had no splits). Daily highs and lows from the
regular session only (9:30-16:00).
Levels: box 1 = the previous session's high and low, box 2 = the session before's. Tops = the two highs,
bottoms = the two lows; the outer top is the higher high, the outer bottom the lower low.
Entry: a 5-minute bar whose range touches a top (low <= level <= high) and closes within 0.1% of it -> short at
its close; the same at a bottom -> long. No other confirmation. If the bar qualifies at both levels on one side,
the level nearer the close is traded; if it qualifies at a top and a bottom, no trade. At most one trade per
level per stock per day and one open position per stock (a new entry needs the previous exit minute to have
ended). Breakout: once a 5-minute bar closes more than 0.1% beyond an outer level, no new trades in that stock
that day.
Stop: 0.1% beyond the outer level on the trade's side; if the two levels on that side are within 0.1% of each
other, 0.1% beyond the touched level. Filled at the stop, or at the minute's open if it opens through.
Target: the far side of the box whose level was touched (box 1 top -> box 1 low, and so on), filled at the
target only when a 1-minute bar trades at least $0.01 through it. A setup whose target is not beyond the entry
is not traded. If one minute touches both stop and target, the stop counts. Otherwise out at the time exit (the
close of the last 1-minute bar before it).
V (video): entries decided 9:35-15:30, time exit 15:55 (half days: 12:30 and 12:55). No filters.
M (machine-style): entries decided 9:35-11:50, time exit 12:00; FOMC decision days skipped (config.yaml); BEA
GDP release days skipped (all estimates, from bea.gov's news archive); jobs and CPI days NOT skipped (bls.gov
refuses automated access and FRED could not be reached); a stock is skipped on its earnings day and the next
session (Alpha Vantage's historical report dates; all reports are treated as after the close, see the report).
In the account view, no new trades that day once the day's realized loss reaches 20% of its opening equity.
R = |entry - stop|. Costs per share: T18's measured average quoted spread for that stock and year (as a fraction
of price) paid in full at entry and again on stop exits (targets are limit orders; time exits pay none, as
specified), plus the SEC and FINRA sale fees (T14's tables) on the sale side (a short's entry, a long's exit);
no commission. Result = (side x (exit - entry) - costs) / R.
Controls, at the same stock, moment, entry price, R and time exit: the opposite direction (stop R away on the
other side, target mirrored at the same distance), and a random direction (seed fixed; it equals the trade or
its opposite).
Account view: $2,500, 1% of the day's opening equity risked per trade (whole shares), intraday buying power 4x
the day's opening equity ($10,000 at the start) shared by the open positions; profits compound daily.

---

Full per-trade tables: [history/2026-10-30-t20-whales.md](history/2026-10-30-t20-whales.md)
