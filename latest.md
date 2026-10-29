T15 OUTCOME: NO PASS

# T15: "Quick Flip Scalper" (fading a large first 15-minute candle), 2016-2023

Run 2026-10-29. One-off test; pass bars fixed in advance; the 2024-2025 holdout was not touched; rulebook.yaml unchanged. The verdict uses the stated setup: 5-minute signal bars and a box of at least 0.25x the 14-day ATR, under the strict entry-minute rule, after the T14 calibrated costs. The 1-, 2- and 3-minute bars and the 0.22x box are reported alongside but do not decide the outcome.

## Findings

- **No universe holds.** On the stated setup (5-minute bars, box >= 0.25x ATR, strict rule) the average trade loses after costs in every universe and every year: all9 -0.37R (z -7.6), spy -0.99R (z -6.8, only 192 trades), stocks in play -0.21R (z -7.2). 0 of 8 years are positive anywhere.
- **It loses before costs too.** Gross R (no slippage, no fees) is -0.21 (all9), -0.67 (spy) and -0.11 (stocks in play). The fade's far-side target (median 4.6-5.7R away) is reached in only 8-15% of trades; 73-81% are stopped.
- **Costs make it worse because the stops are tight.** The median stop is 0.27% of price on all9, 0.12% on SPY and 0.61% on stocks in play, so T14's calibrated slippage costs 0.16R, 0.33R and 0.10R per trade.
- **"Beating the opposite direction" is not an edge here.** The opposite-direction control enters on the other side of the quote, where T14 measured much larger slippage (0.13-0.39% of price vs 0.03-0.07%); with stops this tight that alone costs it several tenths of an R. Stocks in play clears that check (z +4.6) while still losing money itself.
- **No other bar size or box threshold helps.** The 1-, 2- and 3-minute bars are worse (more, smaller trades with higher cost in R), and the 0.22x box changes little. None of the 24 variants would meet even the single-universe bar.
- **The entry-minute rule hardly matters:** close and strict differ by at most 0.01R on 5-minute bars and 0.1R on 1-minute bars.

## Pass bar (5-minute bars, box >= 0.25x ATR, strict rule, after costs)

| Universe | Trades | Avg R after costs | z | Years positive | Beats opposite by (R) | z vs opposite | Holds |
|---|---|---|---|---|---|---|---|
| all9 (9 symbols) | 2959 | -0.367 | -7.6 | 0 of 8 | +0.236 | +2.8 | no |
| spy | 192 | -0.994 | -6.8 | 0 of 8 | +0.133 | +0.5 | no |
| stocks in play (T13 top 20) | 6124 | -0.209 | -7.2 | 0 of 8 | +0.219 | +4.6 | no |

Universes holding: 0 of 3 (needed: 2).

| Universe | at least 300 trades | avg R after costs >= 3 SE above zero (strict) | positive in at least 6 of 8 years (strict) | beats the opposite direction by >= 3 SE (strict) |
|---|---|---|---|---|
| all9 (9 symbols) | yes | no | no | no |
| spy | no | no | no | no |
| stocks in play (T13 top 20) | yes | no | no | yes |

## Every bar size and box threshold (reported; not part of the verdict)

| Universe | Bars | Box | Trades | Strict: avg R | z | Years + | z vs opposite | Close rule: avg R | z | Gross R (strict) | Opposite avg R (strict) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| all9 | 5m | 0.25 | 2959 | -0.367 | -7.6 | 0 | +2.8 | -0.366 | -7.6 | -0.210 | -0.603 |
| all9 | 5m | 0.22 | 3247 | -0.390 | -8.4 | 0 | +2.8 | -0.388 | -8.4 | -0.226 | -0.614 |
| all9 | 1m | 0.25 | 7180 | -0.837 | -18.4 | 0 | +11.4 | -0.754 | -15.4 | -0.497 | -1.691 |
| all9 | 1m | 0.22 | 7879 | -0.862 | -19.8 | 0 | +12.4 | -0.780 | -16.8 | -0.511 | -1.744 |
| all9 | 2m | 0.25 | 5735 | -0.648 | -15.9 | 0 | +6.7 | -0.630 | -15.2 | -0.401 | -1.128 |
| all9 | 2m | 0.22 | 6286 | -0.678 | -17.2 | 0 | +7.0 | -0.659 | -16.5 | -0.421 | -1.162 |
| all9 | 3m | 0.25 | 4589 | -0.537 | -13.2 | 0 | +3.1 | -0.533 | -13.0 | -0.339 | -0.765 |
| all9 | 3m | 0.22 | 5031 | -0.551 | -14.1 | 0 | +3.7 | -0.544 | -13.8 | -0.347 | -0.813 |
| spy | 5m | 0.25 | 192 | -0.994 | -6.8 | 0 | +0.5 | -0.994 | -6.8 | -0.668 | -1.127 |
| spy | 5m | 0.22 | 254 | -1.077 | -8.4 | 0 | +0.9 | -1.077 | -8.4 | -0.717 | -1.288 |
| spy | 1m | 0.25 | 477 | -1.688 | -10.9 | 0 | +9.1 | -1.600 | -9.8 | -0.973 | -3.754 |
| spy | 1m | 0.22 | 629 | -1.642 | -11.6 | 0 | +11.3 | -1.552 | -10.4 | -0.894 | -3.925 |
| spy | 2m | 0.25 | 397 | -1.383 | -10.3 | 0 | +4.8 | -1.383 | -10.3 | -0.868 | -2.429 |
| spy | 2m | 0.22 | 525 | -1.406 | -11.5 | 0 | +6.4 | -1.407 | -11.5 | -0.855 | -2.635 |
| spy | 3m | 0.25 | 304 | -1.190 | -8.5 | 0 | +2.1 | -1.177 | -8.3 | -0.772 | -1.684 |
| spy | 3m | 0.22 | 398 | -1.204 | -9.7 | 0 | +3.5 | -1.194 | -9.6 | -0.766 | -1.912 |
| sip | 5m | 0.25 | 6124 | -0.209 | -7.2 | 0 | +4.6 | -0.203 | -6.9 | -0.108 | -0.428 |
| sip | 5m | 0.22 | 6200 | -0.210 | -7.3 | 0 | +4.8 | -0.204 | -7.0 | -0.108 | -0.435 |
| sip | 1m | 0.25 | 15043 | -0.483 | -11.4 | 0 | +11.9 | -0.383 | -7.6 | -0.219 | -1.262 |
| sip | 1m | 0.22 | 15220 | -0.492 | -11.7 | 0 | +12.0 | -0.389 | -7.8 | -0.226 | -1.269 |
| sip | 2m | 0.25 | 11824 | -0.319 | -11.0 | 0 | +10.2 | -0.298 | -9.8 | -0.153 | -0.781 |
| sip | 2m | 0.22 | 11972 | -0.323 | -11.1 | 0 | +10.4 | -0.300 | -9.9 | -0.156 | -0.788 |
| sip | 3m | 0.25 | 9398 | -0.245 | -8.6 | 0 | +7.4 | -0.234 | -8.1 | -0.112 | -0.633 |
| sip | 3m | 0.22 | 9509 | -0.250 | -8.8 | 0 | +7.4 | -0.239 | -8.4 | -0.116 | -0.634 |

Variants that would meet the single-universe bar: none.

## By year (5-minute bars, box >= 0.25x ATR, strict rule)

| Universe | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 |
|---|---|---|---|---|---|---|---|---|
| all9 | -0.37 (381) | -0.59 (375) | -0.38 (358) | -0.53 (371) | -0.22 (315) | -0.40 (379) | -0.13 (395) | -0.30 (385) |
| spy | -1.02 (30) | -1.84 (26) | -0.16 (20) | -1.49 (26) | -1.12 (10) | -0.64 (31) | -0.83 (30) | -0.76 (19) |
| sip | -0.26 (703) | -0.27 (730) | -0.12 (757) | -0.09 (815) | -0.18 (735) | -0.22 (835) | -0.28 (782) | -0.27 (767) |

## By pattern and side (5-minute bars, box >= 0.25x ATR, strict rule)

| Universe | Pattern | Side | Trades | Avg R after costs | z | Gross R | Target / stop / close |
|---|---|---|---|---|---|---|---|
| all9 | engulfing | short | 1183 | -0.306 | -3.7 | -0.137 | 12.9% / 75.8% / 11.2% |
| all9 | engulfing | long | 1047 | -0.372 | -4.9 | -0.235 | 12.5% / 75.5% / 12.0% |
| all9 | hammer | short | 362 | -0.480 | -3.8 | -0.290 | 13.0% / 79.3% / 7.7% |
| all9 | hammer | long | 367 | -0.435 | -3.9 | -0.298 | 12.5% / 77.7% / 9.8% |
| spy | engulfing | short | 73 | -0.929 | -3.3 | -0.551 | 15.1% / 80.8% / 4.1% |
| spy | engulfing | long | 70 | -0.987 | -5.4 | -0.732 | 15.7% / 78.6% / 5.7% |
| spy | hammer | short | 26 | -0.809 | -1.6 | -0.403 | 19.2% / 76.9% / 3.8% |
| spy | hammer | long | 23 | -1.434 | -4.6 | -1.141 | 4.3% / 95.7% / 0.0% |
| sip | engulfing | short | 2111 | -0.246 | -5.2 | -0.143 | 7.7% / 72.1% / 20.2% |
| sip | engulfing | long | 2256 | -0.175 | -3.5 | -0.081 | 7.4% / 73.0% / 19.5% |
| sip | hammer | short | 858 | -0.178 | -2.3 | -0.067 | 10.3% / 71.7% / 18.1% |
| sip | hammer | long | 899 | -0.237 | -3.1 | -0.132 | 9.1% / 76.5% / 14.3% |

## Trade shape and costs (5-minute bars, box >= 0.25x ATR)

| Universe | Median R (% of price) | Median target distance (R) | Win rate (strict) | Exits: target / stop / close (strict) | Cost per trade (R): strict gross - net | Random-direction gap (R), z |
|---|---|---|---|---|---|---|
| all9 | 0.27% | 4.63 | 22.1% | 12.7% / 76.3% / 10.9% | 0.156 | +0.137, +2.7 |
| spy | 0.12% | 4.16 | 16.7% | 14.6% / 81.2% / 4.2% | 0.327 | +0.055, +0.3 |
| sip | 0.61% | 5.73 | 24.6% | 8.2% / 73.0% / 18.8% | 0.101 | +0.134, +4.1 |

## Funnel (stock-days, 5-minute bars)

| Universe | Stock-days | Flat box | Box < 0.22x ATR | No entry | Fill beyond stop/target | Trades (>= 0.22) | Trades (>= 0.25) |
|---|---|---|---|---|---|---|---|
| all9 | 18108 | 169 | 2246 | 12437 | 0 | 3247 | 2959 |
| spy | 2012 | 8 | 888 | 861 | 0 | 254 | 192 |
| sip | 39885 | 264 | 719 | 32700 | 0 | 6200 | 6124 |

## Method

python -m backtest.bench.t15 run --universe bench       # all9 and spy -> reports/bench/t15/bench.pkl
    python -m backtest.bench.t15 run --universe sip         # T13 stocks-in-play top 20 -> reports/bench/t15/sip.pkl
    python -m backtest.bench.t15 report --md full.md --compact compact.md --findings findings.md
Box: the 9:30-9:45 candle (1-minute bars 9:30-9:44). It counts if its high-low range is at least 0.25x the
14-day daily ATR (known before the open; 0.22x also reported). An up candle -> shorts above the box high only;
a down candle -> longs below the box low only; a flat candle -> no trade. Signal bars: 5-minute bars (also 1, 2
and 3), anchored at 9:45, that start at or after 9:45 and end by 11:00; earlier bars of the same size (from
9:30) count as the bars before a signal. The signal bar must close outside the box (below the low for longs,
above the high for shorts).
Hammer (long): the two bars before it each closed lower than the bar before them; lower wick >= 2x body; upper
wick <= body; close in the top third of the bar's range. Entry: the first later 1-minute bar that trades above
the hammer's high; stop at its low. Inverted hammer (short): the mirror image.
Bullish engulfing (long): a green bar whose body covers the previous bar's red body (open <= previous close,
close >= previous open). Entry: the first later 1-minute bar that trades at the previous bar's high; stop at
the engulfing bar's low. Bearish engulfing: the mirror image.
A setup waits for its entry until 11:00 and is cancelled if a 1-minute bar touches its stop first. The trade
is the setup whose entry comes first; one trade per stock-day. Fill: the entry level, or the minute's open if
it opens beyond it, plus the T14 calibrated entry slippage for the price band. R = fill - stop (before
slippage). Target: the box's far side (the high for longs, the low for shorts), a limit order filled at that
price with no extra cost. Stop: at the stop, or the minute's open if it opens through, minus the T14
calibrated stop slippage. If a minute touches both, the stop counts. Otherwise the exit is the close of the
15:59 bar. Fees: the SEC and FINRA sale fees (T14). Entry minute: "close" counts it as stopped only if it
closes beyond the stop, "strict" counts any touch; the target counts there only on a close beyond it.
Controls: the same stock, moment and R in the opposite direction (target mirrored at the same distance, with
T14's control slippage, i.e. the other side of the quote); and a random direction (seed fixed).
Prices: all9/spy use the bench's split-adjusted bars converted to the day's actual prices (Alpaca's daily
raw close / adjusted close; SPY and QQQ had no splits); the price band uses actual prices. FOMC days are kept.

Costs (T14, from 4,000 tick-replayed trades): mean entry slippage beyond the level and mean stop slippage, as % of price, by price band ($5-10 to $100+), separately for the signal side and for the opposite side at the same moment. Statistics: standard errors clustered by day. Bench symbols: the first 14 sessions of 2016 have no ATR (no 2015 data), so they are skipped.

---

Full per-trade tables: [history/2026-10-29-t15-quick-flip.md](history/2026-10-29-t15-quick-flip.md)
