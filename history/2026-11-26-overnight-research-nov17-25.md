BENCH CHECK: OK (2026-11-26 20:46, code dda41a0, fingerprint 537fb25f1739)

# Overnight research Nov 17-25: replay fills, trade export, variants, missed moves

## Summary in plain English

**Caveat:** this is seven trading days and 77 live trades. Every difference below is small next to the day-to-day swings. Nov 17-18 were Version 1 days live, so the variant replays there run Version 2 on them with modelled option quotes only. Nothing here is a tested rule change yet.

**A. How close the replay gets to live.** With the new fills (buy at the ask and sell at the bid of the quote the live engine saw, the minute sweep next, a model last), the replay repeats live closely on the five Version 2 days:
- 70 of 74 live trades come back (same name, side, entry within 2 min).
- 60 of those 70 are within $5 of the live P&L.
- Day gaps run from $23 to $131. Over the five days live made -$84 and the replay +$160. Most of the gap is a few trades that differ on Nov 19 and Nov 25.

**B. Per-second prices.** Backfilled for all six names, Nov 17-25, 9:25-12:32: about 10,000 seconds per name per day, in per_second/.

**C. Winners vs losers.**
- **The best entry-time signs are weak.** They are a shorter wait after the turning point (winners median 1.48 ATR from the turn, losers 1.87) and a calmer last 15 minutes (2.66 vs 3.01 ATR range). Neither splits winners from losers cleanly (separation about 0.35 on a 0-1 scale).
- **Trend fields barely separate** (SMA 50 and EMA 20 slope, price vs VWAP). The entry shape was "yes" on every trade, so it tells nothing.
- **The trend hypothesis points the right way but is not proven.** Pullbacks inside a clear trend won 31% of the time (+$409); the rest won 20% (+$96). Version 2 trades without the stale-quote ones: 30% (+$408) vs 18% (-$463). The chance of a gap this size by luck is about 1 in 5 (p = 0.19), so it is not significant on this sample.

**C. Variant replays** (all with the new fills; base = current rules without the loss stop, +$996 over the seven days):

| Variant | Total vs base | Result |
|---|---|---|
| Trend filter (clear trend only) | +$398 | Best of the honest variants. Cuts losers from 46 (-$1,713) to 35 (-$1,154); drops 2 of the 13 audited winners. |
| Near the turn, at most 1.75 ATR | +$563 | Looks best, but the 1.75 was picked on these same trades: fitted, not tested. |
| ATR from bars after 9:45 | +$157 | Small gain, mostly Nov 23. |
| -8% loss stop | +$90 | Helped Nov 18 and Nov 25; hurt Nov 19 (-$304 vs -$120). |
| Two-stage exit after 3x the stop | -$177 to -$439 | Best with 30-second candles (-$177). |
| Two-stage exit after 2x the stop | -$894 to -$971 | Clearly worse: it cuts the winners short. |
| Re-entry without the 5-min wait | -$293 | Worse. |
| Max 2 same-direction trades | -$433 | Worse. |
| No RSI-dip step | -$428 | Worse. |

**Entry speed.** From the bar's close to the fill takes 4.3 s (median):
- 3.6 s waiting for the minute bar to arrive from the data feed;
- about 0.4 s for the indicators and checks;
- 0.15 s for the contract, quote and pre-order checks;
- 0.07 s for the fill.

Almost all the delay is the bar feed, not our code.

**D. Missed moves (9:45-11:50).**
- **$1.00 threshold:** there were 1,010 stock moves of at least $1.00 within 10 minutes. A trade the right way was open on 123 of them; one trade can cover several moves. $1.00 is small for SPY and QQQ, so most of these are ordinary wiggles. Where the rules said no, the first step that failed was most often VWAP (376), then trend (260), then setup (146) and momentum (84).
- **5x ATR threshold:** there were 36 large moves, and we were in 7. On those 7 we entered a median 261 s after the move started and still caught 77% of it. The 29 we missed were blocked mostly at the trend step (12) and the VWAP step (10). These are mostly reversals: the big move starts while price is still on the wrong side of VWAP or the averages, which the pullback rule is built to avoid.

**E. Charts.** 308 charts: every trade at 1 minute and at 30, 15 and 10 seconds, in charts/<day>/.

**Where to look first:**
- C's variant table and its split by audited winners, other winners and losers;
- export/all_trades.csv, one row per trade with every field;
- missed/missed_moves.csv, every move with the failed rule step and its numbers.



## A. Replay with live-like fills vs live, per day

Fill model (from the live paper fills: 71 of 74 Version 2 entries filled exactly at the ask of the quote at the order, exits at its bid): buy at the ask, sell at the bid of the quote the engine would have seen. That quote is the live engine's own record for the same contract within 3 s (the same moment as a live order), else the every-minute quote sweep of that contract (at most 60 s old, real quote time, so Nov 19's stale overnight quotes come back), else the last option trade +/- the estimated spread. Rules as live ran: no loss stop, no quote-age check, AMZN traded. Nov 17-18 were Version 1 live (the replay runs Version 2), so their rows don't compare.

| Day | Live engine | Live trades | Replay trades | Matched | Live P&L | Replay P&L | Gap | Matched gap | Matched within $5 | Fills from live/sweep/model |
|---|---|---|---|---|---|---|---|---|---|---|
| 2026-11-17 | V1 | 2 | 19 | 0 | +612 | +1,042 | +430 | 0.00 | 0/0 | 0/0/38 |
| 2026-11-18 | V1 | 1 | 22 | 0 | -23 | -323 | -300 | 0.00 | 0/0 | 0/0/44 |
| 2026-11-19 | V2 | 20 | 17 | 17 | -268 | -174 | +94 | +64 | 15/17 | 32/2/0 |
| 2026-11-20 | V2 | 9 | 9 | 9 | +338 | +283 | -55 | -55 | 8/9 | 17/0/1 |
| 2026-11-23 | V2 | 18 | 18 | 18 | +488 | +539 | +51 | +51 | 15/18 | 32/2/2 |
| 2026-11-24 | V2 | 14 | 14 | 14 | -52 | -29 | +23 | +23 | 12/14 | 26/0/2 |
| 2026-11-25 | V2 | 13 | 15 | 12 | -590 | -459 | +131 | -2.00 | 10/12 | 22/6/2 |

Version 2 days: live -84, replay +160; 70 of 74 live trades matched (same name and side, entry within 2 min), 3 replay trades with no live match.

## B. Per-second stock prices, Nov 17-25

From Alpaca's SIP trade history (last-sale trades only, cancelled ones dropped), the last trade of each second, 9:25-12:32, six names. Seconds without a trade are left out (the price stands). Saved as per_second/<day>.csv.gz (time, name, price).

| Day | AAPL | AMZN | NVDA | QQQ | SPY | TSLA |
|---|---|---|---|---|---|---|
| 2026-11-17 | 9703 | 10024 | 10800 | 10583 | 10599 | 9820 |
| 2026-11-18 | 9095 | 10297 | 10799 | 10415 | 10323 | 9756 |
| 2026-11-19 | 9994 | 10400 | 10794 | 10612 | 10610 | 9935 |
| 2026-11-20 | 10207 | 10456 | 10800 | 10782 | 10756 | 10445 |
| 2026-11-23 | 9946 | 10295 | 10800 | 10641 | 10713 | 10438 |
| 2026-11-24 | 9696 | 9659 | 10800 | 10673 | 10685 | 10112 |
| 2026-11-25 | 10337 | 10653 | 10800 | 10762 | 10696 | 10318 |

## C. All trades, winners vs losers, and the variants

all_trades.csv: 77 trades (3 Version 1 on Nov 17-18, 5 Nov 19 trades before 10:30 flagged as stale-quote trades); 13 audited winners, 6 other winners, 58 losers.

### Winners vs losers, field by field

Separation: 0 = the field doesn't tell winners from losers, 1 = it splits them perfectly (2 x |AUC - 0.5|; AUC = the chance a random winner's value is higher than a random loser's). Fields known only after the entry (give-back, best move, hold) separate by construction and are marked.

| field | winners | losers | auc | separation | at_entry |
|---|---|---|---|---|---|
| giveback_pct | median 42.9 (19) | median 100 (58) | 0.03 | 0.94 | False |
| mfe_atr | median 3.41 (19) | median 1.02 (58) | 0.94 | 0.88 | False |
| mae_usd | median 0.0801 (19) | median 0.58 (58) | 0.20 | 0.60 | False |
| hold_s | median 529 (19) | median 450 (58) | 0.68 | 0.35 | False |
| range15_atr | median 2.66 (19) | median 3.01 (58) | 0.33 | 0.35 | True |
| delay_atr | median 1.48 (19) | median 1.87 (58) | 0.33 | 0.34 | True |
| vwap_crosses_15 | median 0 (19) | median 0 (58) | 0.38 | 0.23 | True |
| stock_price_age_s | median 0.66 (19) | median 0.775 (58) | 0.39 | 0.21 | True |
| stop_vs_945 | median 1 (17) | median 1 (57) | 0.60 | 0.20 | True |
| quote_age_s | median 0.15 (19) | median 0.185 (58) | 0.40 | 0.19 | True |
| same_dir_count | median 0 (19) | median 1 (58) | 0.41 | 0.19 | True |
| atr_1m | median 0.949 (19) | median 0.816 (58) | 0.59 | 0.17 | True |
| delay_bars | median 3 (19) | median 4 (58) | 0.42 | 0.17 | True |
| stop_distance | median 1.17 (17) | median 1.24 (57) | 0.58 | 0.16 | True |
| dist_sma50_atr | median 1.72 (19) | median 1.57 (58) | 0.56 | 0.12 | True |
| trend_with_trade | 74% yes (19) | 62% yes (58) | 0.56 | 0.12 | True |
| rsi_at_signal | median 42 (19) | median 41.8 (58) | 0.45 | 0.10 | True |
| sma50_slope_atr | median 0.524 (19) | median 0.619 (58) | 0.55 | 0.10 | True |
| ema20_slope_atr | median 0.279 (19) | median 0.232 (58) | 0.55 | 0.09 | True |
| price_vs_vwap_atr | median 2.75 (19) | median 2.33 (58) | 0.54 | 0.08 | True |
| bar_close_to_fill_s | median 4.29 (19) | median 4.32 (58) | 0.46 | 0.08 | True |
| near_sma50 | 21% yes (19) | 28% yes (58) | 0.47 | 0.07 | True |
| our_vs_sip_same_second | median 0 (19) | median 0 (58) | 0.47 | 0.06 | True |
| on_our_side_of_vwap | 84% yes (19) | 88% yes (58) | 0.48 | 0.04 | True |
| delay_usd | median 1.5 (19) | median 1.53 (58) | 0.51 | 0.01 | True |
| delay_cost_usd | median 62 (19) | median 53 (58) | 0.51 | 0.01 | True |
| entry_shape | 100% yes (19) | 100% yes (58) | 0.50 | 0.00 | True |

Version 2 only, without the stale-quote trades (known at entry):

| field | winners | losers | auc | separation |
|---|---|---|---|---|
| delay_atr | median 1.47 (16) | median 1.87 (53) | 0.31 | 0.38 |
| range15_atr | median 2.67 (16) | median 2.99 (53) | 0.36 | 0.28 |
| vwap_crosses_15 | median 0 (16) | median 0 (53) | 0.38 | 0.23 |
| stop_vs_945 | median 1 (16) | median 1 (53) | 0.61 | 0.23 |
| stock_price_age_s | median 0.7 (16) | median 0.78 (53) | 0.40 | 0.21 |
| stop_distance | median 1.32 (16) | median 1.24 (53) | 0.60 | 0.20 |
| atr_1m | median 0.883 (16) | median 0.828 (53) | 0.60 | 0.20 |
| delay_bars | median 3 (16) | median 4 (53) | 0.41 | 0.18 |
| sma50_slope_atr | median 0.572 (16) | median 0.607 (53) | 0.57 | 0.13 |
| quote_age_s | median 0.14 (16) | median 0.17 (53) | 0.44 | 0.13 |

### The trend hypothesis

Clear trend = pullback (or failed bounce) with SMA 50 and EMA 20 both moving our way over 10 bars and at most 1 VWAP cross in 15 bars.

- All trades: in a clear trend 10 winners / 22 losers (31% win rate, P&L +409); the rest 9 / 36 (20%, +96). 53% of winners vs 38% of losers were in a clear trend; one-sided Fisher p = 0.19.
- Version 2, no stale-quote trades: in a clear trend 9 winners / 21 losers (30% win rate, P&L +408); the rest 7 / 32 (18%, -463). 56% of winners vs 40% of losers were in a clear trend; one-sided Fisher p = 0.19.

### Variant replays, P&L per day (after the $2 commission)

Every variant runs the current engine (quote-age check on, AMZN watch only) with the fill model of A, the loss stop off unless named. Two-stage: once the stock has run 2x or 3x the stop distance, the trade also exits at the first of a 0.5 x ATR trail from the best price, 2 of the last 3 candles against us, or an engulfing candle against us (candles of the size named, from per-second prices). Nov 17-18 are Version 2 replays of Version 1 days. The near-turn filter's 1.75 ATR was chosen on these same trades: fitted, not tested.

| Variant | 11-17 | 11-18 | 11-19 | 11-20 | 11-23 | 11-24 | 11-25 | Total |
|---|---|---|---|---|---|---|---|---|
| Live (for reference) | +612 | -23 | -268 | +338 | +488 | -52 | -590 | +505 |
| Base: current rules, no loss stop | +1,057 | -328 | -120 | +315 | +637 | -40 | -525 | +996 |
| Loss stop -8% | +1,057 | -260 | -304 | +315 | +637 | -40 | -319 | +1,086 |
| ATR from 9:45 | +1,011 | -303 | -135 | +315 | +792 | -51 | -476 | +1,153 |
| No RSI dip step | +999 | -563 | -172 | +864 | +277 | -319 | -518 | +568 |
| Re-entry, no 5-min wait | +1,056 | -423 | -211 | +331 | +536 | -58 | -528 | +703 |
| Max 2 same direction (SPY+QQQ = 1) | +589 | -350 | -45 | +310 | +474 | -4.00 | -411 | +563 |
| Trend filter (clear trend) | +1,147 | -102 | -388 | +293 | +790 | +67 | -413 | +1,394 |
| Near the turn, <= 1.75 ATR (fitted) | +626 | -312 | +132 | +333 | +934 | +62 | -216 | +1,559 |
| Two-stage after 2x stop, 60s candles | +297 | -283 | -226 | +219 | +583 | -40 | -525 | +25 |
| Two-stage after 2x stop, 30s candles | +379 | -283 | -226 | +182 | +615 | -40 | -525 | +102 |
| Two-stage after 2x stop, 15s candles | +325 | -269 | -226 | +182 | +598 | -40 | -525 | +45 |
| Two-stage after 2x stop, 10s candles | +310 | -274 | -226 | +180 | +624 | -40 | -525 | +49 |
| Two-stage after 3x stop, 60s candles | +643 | -328 | -216 | +287 | +827 | -40 | -525 | +648 |
| Two-stage after 3x stop, 30s candles | +814 | -328 | -216 | +287 | +827 | -40 | -525 | +819 |
| Two-stage after 3x stop, 15s candles | +611 | -328 | -216 | +238 | +817 | -40 | -525 | +557 |
| Two-stage after 3x stop, 10s candles | +797 | -328 | -216 | +238 | +823 | -40 | -525 | +749 |

### The same, split by what the trade was live

Each replay trade is matched to the live trade it repeats (same name and side, entry within 2 min); 'new trade' = no live trade like it. Count: P&L.

| Variant | audited winner (n) | other winner (n) | loser (n) | new trade (n) |
|---|---|---|---|---|
| Live (for reference) | 13: +1,750 | 6: +817 | 58: -2,062 | - |
| Base: current rules, no loss stop | 13: +1,796 | 3: +184 | 46: -1,713 | 34: +729 |
| Loss stop -8% | 12: +1,508 | 3: +184 | 34: -1,403 | 19: +797 |
| ATR from 9:45 | 13: +1,881 | 3: +184 | 45: -1,620 | 34: +708 |
| No RSI dip step | 11: +1,422 | 3: +184 | 40: -1,440 | 106: +402 |
| Re-entry, no 5-min wait | 13: +1,796 | 4: +202 | 46: -1,737 | 57: +442 |
| Max 2 same direction (SPY+QQQ = 1) | 11: +1,599 | 3: +184 | 34: -1,431 | 33: +211 |
| Trend filter (clear trend) | 11: +1,422 | 3: +184 | 35: -1,154 | 30: +942 |
| Near the turn, <= 1.75 ATR (fitted) | 10: +1,709 | 2: +83 | 16: -453 | 28: +220 |
| Two-stage after 2x stop, 60s candles | 13: +1,540 | 3: +184 | 46: -1,713 | 34: +14 |
| Two-stage after 2x stop, 30s candles | 13: +1,535 | 3: +184 | 46: -1,713 | 34: +96 |
| Two-stage after 2x stop, 15s candles | 13: +1,518 | 3: +184 | 46: -1,713 | 34: +56 |
| Two-stage after 2x stop, 10s candles | 13: +1,542 | 3: +184 | 46: -1,713 | 34: +36 |
| Two-stage after 3x stop, 60s candles | 13: +1,862 | 3: +184 | 46: -1,713 | 34: +315 |
| Two-stage after 3x stop, 30s candles | 13: +1,862 | 3: +184 | 46: -1,713 | 34: +486 |
| Two-stage after 3x stop, 15s candles | 13: +1,803 | 3: +184 | 46: -1,713 | 34: +283 |
| Two-stage after 3x stop, 10s candles | 13: +1,809 | 3: +184 | 46: -1,713 | 34: +469 |

### Entry speed (live, all 77 trades)

From the bar's close: the bar arriving (the engine's bar delay), the indicators and rule checks (to the signal being logged), the contract choice + quote + pre-order checks (to the order), and the fill. The engine logs no separate time for indicators vs checks or contract vs quote, so those come in pairs.

| seconds | bar_arrival_s | checks_s | contract_quote_checks_s | order_to_fill_s | bar_close_to_fill_s |
|---|---|---|---|---|---|
| mean | 3.55 | 0.49 | 0.18 | 0.09 | 4.30 |
| 50% | 3.60 | 0.42 | 0.15 | 0.07 | 4.30 |
| min | 3.00 | 0.25 | 0.05 | 0.01 | 3.57 |
| max | 4.00 | 1.72 | 0.71 | 0.60 | 5.99 |

## D. Missed opportunities, 9:45-11:50

Moves of at least $1.00, and separately of at least 5x the name's 1-minute ATR, within 600 s, from the per-second prices (missed_moves.csv has every move: start/end, size, traded or not, entry vs the start, $ captured, and for the untraded ones the rule steps on the last closed bar before the start, with the numbers).

### Threshold $1.00

1010 moves, 123 traded the right way (one trade can cover several moves); on those, entry a median 25 s before the move's start (a trade already open when the move began counts), capturing a median 56% of it.

| day | Moves | Traded |
|---|---|---|
| 2026-11-17 | 129 | 4 |
| 2026-11-18 | 137 | 1 |
| 2026-11-19 | 130 | 23 |
| 2026-11-20 | 146 | 18 |
| 2026-11-23 | 160 | 36 |
| 2026-11-24 | 148 | 21 |
| 2026-11-25 | 160 | 20 |

| name | Moves | Traded | Avg_size |
|---|---|---|---|
| AAPL | 101 | 16 | 1.28 |
| AMZN | 118 | 7 | 1.39 |
| NVDA | 130 | 22 | 1.49 |
| QQQ | 234 | 27 | 2.10 |
| SPY | 207 | 23 | 1.74 |
| TSLA | 220 | 28 | 1.79 |

| What the rules showed at the start | Moves |
|---|---|
| regular 1_vwap | 376 |
| regular 2_trend | 260 |
| regular 3_setup | 146 |
| regular 4_momentum | 84 |
| signal (pullback) on this bar | 7 |
| chop filter | 7 |
| regular rules off (only the squeeze rule enters before 10:00) | 6 |
| signal (squeeze) on this bar | 1 |

| First failed step (regular rule) | Moves |
|---|---|
| 1_vwap | 376 |
| 2_trend | 260 |
| 3_setup | 146 |
| 4_momentum | 85 |

### Threshold 5x ATR

36 moves, 7 traded the right way (one trade can cover several moves); on those, entry a median 261 s after the move's start (a trade already open when the move began counts), capturing a median 77% of it.

| day | Moves | Traded |
|---|---|---|
| 2026-11-17 | 13 | 2 |
| 2026-11-18 | 2 | 0 |
| 2026-11-19 | 10 | 2 |
| 2026-11-20 | 3 | 0 |
| 2026-11-23 | 3 | 2 |
| 2026-11-24 | 1 | 1 |
| 2026-11-25 | 4 | 0 |

| name | Moves | Traded | Avg_size |
|---|---|---|---|
| AAPL | 3 | 0 | 2.30 |
| AMZN | 7 | 1 | 3.03 |
| NVDA | 3 | 0 | 2.10 |
| QQQ | 10 | 3 | 6.07 |
| SPY | 9 | 2 | 4.85 |
| TSLA | 4 | 1 | 4.85 |

| What the rules showed at the start | Moves |
|---|---|
| regular 2_trend | 12 |
| regular 1_vwap | 10 |
| regular 4_momentum | 3 |
| regular 3_setup | 3 |
| signal (squeeze) on this bar | 1 |

| First failed step (regular rule) | Moves |
|---|---|
| 2_trend | 12 |
| 1_vwap | 11 |
| 4_momentum | 3 |
| 3_setup | 3 |

## E. Charts

308 charts in charts/<day>/: every trade at 1 minute and at 30, 15 and 10 seconds, with VWAP, EMA 8/20, SMA 50, Bollinger 20/2, Keltner 20/1.5 x ATR, RSI 9, the trailing-stop line (Version 2), the turning point, entry, best price and exit. Version 1 trades (Nov 17-18) had an option stop: no stock-stop line.

## asis

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 114 | 31.6% | $+103.92 | $-36.69 | $+879.00 | $+7.71 | $+673.00 | $-102.00 | $+1,042.00 | $-459.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 86 | 31.4% | $+622.00 | $+7.23 |
| squeeze | 28 | 32.1% | $+257.00 | $+9.18 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 23 | 26.1% | $+327.00 | $+14.22 |
| TSLA | 19 | 31.6% | $+278.00 | $+14.63 |
| AAPL | 17 | 35.3% | $+207.00 | $+12.18 |
| NVDA | 20 | 45.0% | $+116.00 | $+5.80 |
| SPY | 17 | 29.4% | $+78.00 | $+4.59 |
| AMZN | 18 | 22.2% | $-127.00 | $-7.06 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 114 | 31.6% | $+879.00 | $+7.71 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 85 | 36.5% | $+1,291.00 | $+15.19 |
| long | 29 | 17.2% | $-412.00 | $-14.21 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | AMZN | long | squeeze | AMZN261118C00260000 | 09:54 | 2.37 | 09:56 | 2.12 | trailing_stop | $-27.00 |
| 2 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 3 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 4 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 5 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 6 | 2026-11-17 | AMZN | long | squeeze | AMZN261118C00260000 | 10:12 | 2.70 | 10:16 | 2.49 | trailing_stop | $-23.00 |
| 7 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:50 | 2.95 | trailing_stop | $+118.00 |
| 8 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 9 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:50 | 8.49 | trailing_stop | $+133.00 |
| 10 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:50 | 7.71 | trailing_stop | $+235.00 |
| 11 | 2026-11-17 | AMZN | short | pullback | AMZN261118P00257500 | 11:08 | 4.31 | 11:09 | 4.14 | trailing_stop | $-19.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 13 | 2026-11-17 | AMZN | short | pullback | AMZN261118P00257500 | 11:18 | 4.21 | 11:47 | 4.77 | trailing_stop | $+54.00 |
| 14 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 15 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 16 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 17 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 18 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 19 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 20 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 21 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 22 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 23 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 24 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 25 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 26 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 27 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 28 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 29 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 30 | 2026-11-18 | AMZN | long | pullback | AMZN261118C00262500 | 11:06 | 2.05 | 11:12 | 1.83 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 32 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 33 | 2026-11-18 | AMZN | short | squeeze | AMZN261118P00262500 | 11:18 | 1.02 | 11:21 | 1.02 | trailing_stop | $-2.00 |
| 34 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 35 | 2026-11-18 | AMZN | long | pullback | AMZN261118C00262500 | 11:30 | 1.97 | 11:39 | 2.30 | trailing_stop | $+31.00 |
| 36 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 37 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 38 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 39 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 40 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 41 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 42 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 43 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 44 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 45 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 46 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 47 | 2026-11-19 | AMZN | short | pullback | AMZN261120P00270000 | 10:54 | 4.50 | 10:59 | 4.00 | trailing_stop | $-52.00 |
| 48 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 49 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 50 | 2026-11-19 | AMZN | short | pullback | AMZN261120P00270000 | 11:29 | 3.90 | 11:36 | 3.80 | trailing_stop | $-12.00 |
| 51 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 52 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 53 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.53 | 11:43 | 3.40 | trailing_stop | $-15.00 |
| 54 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 55 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 56 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 57 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 58 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.50 | trailing_stop | $+288.00 |
| 59 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 60 | 2026-11-20 | AMZN | short | pullback | AMZN261120P00257500 | 10:43 | 3.70 | 10:48 | 3.40 | trailing_stop | $-32.00 |
| 61 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 62 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 63 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 64 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 65 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 66 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 67 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 68 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 69 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 70 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 71 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:45 | 4.30 | trailing_stop | $+152.00 |
| 72 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 73 | 2026-11-23 | AMZN | long | pullback | AMZN261123C00257500 | 10:32 | 1.81 | 10:44 | 1.50 | trailing_stop | $-33.00 |
| 74 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 75 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 76 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 77 | 2026-11-23 | AMZN | long | pullback | AMZN261123C00257500 | 11:07 | 1.52 | 11:15 | 1.35 | trailing_stop | $-19.00 |
| 78 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 79 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 80 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 81 | 2026-11-23 | AMZN | long | pullback | AMZN261123C00257500 | 11:21 | 1.47 | 11:32 | 1.03 | trailing_stop | $-46.00 |
| 82 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 83 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:43 | 5.19 | trailing_stop | $+195.00 |
| 84 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 85 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 86 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 87 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 88 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 89 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 90 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 91 | 2026-11-24 | AMZN | short | pullback | AMZN261125P00255000 | 11:01 | 4.55 | 11:09 | 4.90 | trailing_stop | $+33.00 |
| 92 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 93 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 94 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 95 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 96 | 2026-11-24 | AMZN | short | pullback | AMZN261125P00252500 | 11:36 | 3.80 | 11:44 | 3.60 | trailing_stop | $-22.00 |
| 97 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 98 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 99 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 100 | 2026-11-25 | AMZN | short | pullback | AMZN261125P00240000 | 10:17 | 1.90 | 10:30 | 3.03 | trailing_stop | $+111.00 |
| 101 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 102 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 103 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 104 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 105 | 2026-11-25 | AMZN | short | pullback | AMZN261125P00237500 | 10:40 | 2.08 | 10:49 | 2.07 | trailing_stop | $-3.00 |
| 106 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 107 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 108 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 109 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 110 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 111 | 2026-11-25 | AMZN | short | pullback | AMZN261125P00237500 | 11:03 | 2.43 | 11:06 | 2.03 | trailing_stop | $-42.00 |
| 112 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 113 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 114 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## base

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+109.75 | $-39.31 | $+996.00 | $+10.38 | $+673.00 | $-102.00 | $+1,057.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 71 | 32.4% | $+697.00 | $+9.82 |
| squeeze | 25 | 36.0% | $+299.00 | $+11.96 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 23 | 26.1% | $+317.00 | $+13.78 |
| TSLA | 19 | 31.6% | $+278.00 | $+14.63 |
| AAPL | 17 | 35.3% | $+207.00 | $+12.18 |
| NVDA | 20 | 45.0% | $+116.00 | $+5.80 |
| SPY | 17 | 29.4% | $+78.00 | $+4.59 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 96 | 33.3% | $+996.00 | $+10.38 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+1,277.00 | $+17.26 |
| long | 22 | 18.2% | $-281.00 | $-12.77 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:50 | 2.95 | trailing_stop | $+118.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:50 | 8.49 | trailing_stop | $+133.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:50 | 7.71 | trailing_stop | $+235.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.50 | trailing_stop | $+288.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 60 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:45 | 4.30 | trailing_stop | $+152.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 71 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:43 | 5.19 | trailing_stop | $+195.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 83 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## atr945

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 95 | 33.7% | $+113.03 | $-39.11 | $+1,153.00 | $+12.14 | $+673.00 | $-102.00 | $+1,011.00 | $-476.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 71 | 32.4% | $+775.00 | $+10.92 |
| squeeze | 24 | 37.5% | $+378.00 | $+15.75 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 23 | 26.1% | $+355.00 | $+15.43 |
| TSLA | 18 | 33.3% | $+301.00 | $+16.72 |
| AAPL | 17 | 35.3% | $+228.00 | $+13.41 |
| NVDA | 20 | 45.0% | $+170.00 | $+8.50 |
| SPY | 17 | 29.4% | $+99.00 | $+5.82 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 95 | 33.7% | $+1,153.00 | $+12.14 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 73 | 38.4% | $+1,353.00 | $+18.53 |
| long | 22 | 18.2% | $-200.00 | $-9.09 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 2.98 | trailing_stop | $-52.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 5.81 | trailing_stop | $-70.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.85 | trailing_stop | $+29.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.66 | trailing_stop | $-62.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:56 | 3.27 | trailing_stop | $+150.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:50 | 8.43 | trailing_stop | $+127.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:50 | 7.63 | trailing_stop | $+227.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 6.86 | trailing_stop | $-9.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.71 | trailing_stop | $-63.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.72 | trailing_stop | $-67.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:50 | 2.81 | trailing_stop | $+44.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.17 | trailing_stop | $+40.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:46 | 3.41 | trailing_stop | $-18.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:41 | 3.65 | trailing_stop | $+58.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.50 | trailing_stop | $+288.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:35 | 6.50 | trailing_stop | $+199.00 |
| 59 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:35 | 5.75 | trailing_stop | $+190.00 |
| 60 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:32 | 5.62 | trailing_stop | $+145.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:45 | 4.30 | trailing_stop | $+152.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:43 | 2.85 | trailing_stop | $-6.00 |
| 63 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 64 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 65 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 66 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 67 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 68 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 69 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 70 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:43 | 5.19 | trailing_stop | $+195.00 |
| 71 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 72 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 73 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 74 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 75 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 76 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 77 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.23 | trailing_stop | $-19.00 |
| 78 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 79 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 80 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 84 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 85 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 86 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:34 | 2.36 | trailing_stop | $+1.00 |
| 87 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.77 | trailing_stop | $-84.00 |
| 88 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 89 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 90 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:21 | 3.44 | trailing_stop | $-25.00 |
| 91 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 92 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:13 | 2.43 | trailing_stop | $-5.00 |
| 93 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 94 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 95 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## loss8

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 68 | 35.3% | $+124.54 | $-43.25 | $+1,086.00 | $+15.97 | $+673.00 | $-102.00 | $+1,057.00 | $-319.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 50 | 34.0% | $+748.00 | $+14.96 |
| squeeze | 18 | 38.9% | $+338.00 | $+18.78 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 16 | 31.2% | $+569.00 | $+35.56 |
| AAPL | 13 | 38.5% | $+240.00 | $+18.46 |
| NVDA | 14 | 50.0% | $+137.00 | $+9.79 |
| SPY | 10 | 30.0% | $+131.00 | $+13.10 |
| TSLA | 15 | 26.7% | $+9.00 | $+0.60 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 68 | 35.3% | $+1,086.00 | $+15.97 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 52 | 38.5% | $+1,196.00 | $+23.00 |
| long | 16 | 25.0% | $-110.00 | $-6.88 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:50 | 2.95 | trailing_stop | $+118.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:50 | 8.49 | trailing_stop | $+133.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:50 | 7.71 | trailing_stop | $+235.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 13 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 21 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 22 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 23 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 24 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 25 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 26 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 27 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 28 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 29 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 30 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 31 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 32 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 33 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 34 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 35 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 36 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 37 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 38 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 39 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 40 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:45 | 4.30 | trailing_stop | $+152.00 |
| 41 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 42 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 43 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 44 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 45 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 46 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 47 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 48 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 49 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:43 | 5.19 | trailing_stop | $+195.00 |
| 50 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 51 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 52 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 53 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 54 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 55 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 56 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 57 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 58 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 59 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 60 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 61 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 62 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 63 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 64 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 65 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 66 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 67 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 68 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |

## max2

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 81 | 30.9% | $+116.92 | $-42.14 | $+563.00 | $+6.95 | $+673.00 | $-102.00 | $+589.00 | $-411.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 63 | 27.0% | $+297.00 | $+4.71 |
| squeeze | 18 | 44.4% | $+266.00 | $+14.78 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 22 | 27.3% | $+347.00 | $+15.77 |
| AAPL | 14 | 35.7% | $+149.00 | $+10.64 |
| SPY | 16 | 31.2% | $+99.00 | $+6.19 |
| NVDA | 15 | 40.0% | $+3.00 | $+0.20 |
| TSLA | 14 | 21.4% | $-35.00 | $-2.50 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 81 | 30.9% | $+563.00 | $+6.95 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 62 | 33.9% | $+923.00 | $+14.89 |
| long | 19 | 21.1% | $-360.00 | $-18.95 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:50 | 2.95 | trailing_stop | $+118.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 7 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 8 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 9 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 10 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:46 | 7.33 | 11:46 | 7.12 | trailing_stop | $-23.00 |
| 12 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 13 | 2026-11-17 | TSLA | short | pullback | TSLA261118P00380000 | 11:48 | 6.68 | 11:56 | 6.20 | trailing_stop | $-50.00 |
| 14 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 16 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 17 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 18 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 19 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 21 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 22 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 23 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 24 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 25 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 26 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 27 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 28 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 29 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 30 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 31 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 32 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 33 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 34 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 35 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 36 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 37 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 38 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 39 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.50 | trailing_stop | $+288.00 |
| 41 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 42 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 43 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 44 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 45 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 46 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 47 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 48 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 49 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 50 | 2026-11-23 | TSLA | long | pullback | TSLA261123C00392500 | 10:37 | 3.55 | 10:43 | 2.85 | trailing_stop | $-72.00 |
| 51 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 52 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 53 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 54 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 55 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 56 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 57 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:43 | 5.19 | trailing_stop | $+195.00 |
| 58 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 59 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 60 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 61 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 62 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 63 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 64 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00632000 | 11:13 | 3.37 | 11:20 | 3.28 | trailing_stop | $-11.00 |
| 65 | 2026-11-24 | SPY | short | pullback | SPY261124P00713000 | 11:14 | 2.89 | 11:17 | 2.83 | trailing_stop | $-8.00 |
| 66 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 67 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 68 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 69 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 70 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 71 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 72 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 73 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 74 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 75 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 76 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 77 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 78 | 2026-11-25 | AAPL | long | squeeze | AAPL261125C00347500 | 11:15 | 1.23 | 11:28 | 1.88 | trailing_stop | $+63.00 |
| 79 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 80 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 81 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## near_turn

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 56 | 42.9% | $+115.50 | $-37.91 | $+1,559.00 | $+27.84 | $+673.00 | $-88.00 | $+934.00 | $-312.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 47 | 40.4% | $+1,203.00 | $+25.60 |
| squeeze | 9 | 55.6% | $+356.00 | $+39.56 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 9 | 55.6% | $+848.00 | $+94.22 |
| AAPL | 10 | 40.0% | $+220.00 | $+22.00 |
| SPY | 10 | 40.0% | $+199.00 | $+19.90 |
| NVDA | 13 | 61.5% | $+182.00 | $+14.00 |
| TSLA | 14 | 21.4% | $+110.00 | $+7.86 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 56 | 42.9% | $+1,559.00 | $+27.84 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 45 | 44.4% | $+1,300.00 | $+28.89 |
| long | 11 | 36.4% | $+259.00 | $+23.55 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 2 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 3 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 4 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 5 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:20 | 2.85 | 11:55 | 3.19 | trailing_stop | $+32.00 |
| 6 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 7 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00652000 | 11:42 | 3.24 | 11:46 | 3.37 | trailing_stop | $+11.00 |
| 8 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:46 | 7.33 | 11:46 | 7.12 | trailing_stop | $-23.00 |
| 9 | 2026-11-17 | TSLA | short | pullback | TSLA261118P00380000 | 11:48 | 6.68 | 11:56 | 6.20 | trailing_stop | $-50.00 |
| 10 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 11 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 12 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:20 | 3.76 | 10:23 | 3.06 | trailing_stop | $-72.00 |
| 13 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 14 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 15 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 16 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 17 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 18 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 19 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 20 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 21 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:44 | 3.40 | 11:50 | 2.76 | trailing_stop | $-66.00 |
| 22 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:47 | 2.57 | 11:50 | 2.25 | trailing_stop | $-34.00 |
| 23 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 24 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 25 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 26 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 27 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 28 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:23 | 6.20 | 11:28 | 5.40 | trailing_stop | $-82.00 |
| 29 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 30 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.50 | trailing_stop | $+288.00 |
| 31 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 32 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 33 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 34 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 35 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 36 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:25 | 3.10 | 11:55 | 3.65 | trailing_stop | $+53.00 |
| 37 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 38 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 39 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 40 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:45 | 4.30 | trailing_stop | $+152.00 |
| 41 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 42 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 43 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:43 | 5.19 | trailing_stop | $+195.00 |
| 44 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 45 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 46 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 47 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 48 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 49 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:36 | 4.60 | 11:44 | 4.70 | trailing_stop | $+8.00 |
| 50 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 51 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 52 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 53 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:10 | 3.41 | 11:14 | 3.21 | trailing_stop | $-22.00 |
| 54 | 2026-11-25 | QQQ | short | squeeze | QQQ261125P00609000 | 11:10 | 3.37 | 11:21 | 2.81 | trailing_stop | $-58.00 |
| 55 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:41 | 1.55 | 11:50 | 1.64 | trailing_stop | $+7.00 |
| 56 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |

## no_rsi_dip

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 160 | 35.0% | $+80.36 | $-37.81 | $+568.00 | $+3.55 | $+673.00 | $-102.00 | $+999.00 | $-563.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 140 | 34.3% | $+317.00 | $+2.26 |
| squeeze | 20 | 40.0% | $+251.00 | $+12.55 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 34 | 41.2% | $+223.00 | $+6.56 |
| QQQ | 34 | 29.4% | $+150.00 | $+4.41 |
| NVDA | 32 | 40.6% | $+150.00 | $+4.69 |
| AAPL | 31 | 38.7% | $+132.00 | $+4.26 |
| TSLA | 29 | 24.1% | $-87.00 | $-3.00 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 160 | 35.0% | $+568.00 | $+3.55 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 118 | 41.5% | $+1,384.00 | $+11.73 |
| long | 42 | 16.7% | $-816.00 | $-19.43 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | AAPL | long | pullback | AAPL261118C00352500 | 10:03 | 3.85 | 10:04 | 3.67 | trailing_stop | $-20.00 |
| 4 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 5 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00660000 | 10:06 | 3.36 | 10:12 | 3.16 | trailing_stop | $-22.00 |
| 6 | 2026-11-17 | SPY | short | pullback | SPY261117P00738000 | 10:09 | 2.73 | 10:11 | 2.76 | trailing_stop | $+1.00 |
| 7 | 2026-11-17 | AAPL | long | pullback | AAPL261118C00352500 | 10:12 | 4.03 | 10:17 | 3.76 | trailing_stop | $-29.00 |
| 8 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:14 | 6.62 | 10:23 | 6.72 | trailing_stop | $+8.00 |
| 9 | 2026-11-17 | SPY | short | pullback | SPY261117P00737000 | 10:17 | 2.57 | 10:23 | 2.28 | trailing_stop | $-31.00 |
| 10 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:19 | 3.34 | 10:23 | 2.70 | trailing_stop | $-66.00 |
| 11 | 2026-11-17 | SPY | short | pullback | SPY261117P00737000 | 10:29 | 2.56 | 10:34 | 3.41 | trailing_stop | $+83.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 13 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:50 | 8.49 | trailing_stop | $+133.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:50 | 7.71 | trailing_stop | $+235.00 |
| 15 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00355000 | 10:34 | 3.07 | 10:45 | 4.09 | trailing_stop | $+100.00 |
| 16 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 17 | 2026-11-17 | NVDA | long | pullback | NVDA261118C00155000 | 11:18 | 6.39 | 11:22 | 6.36 | trailing_stop | $-5.00 |
| 18 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:23 | 3.61 | 11:29 | 2.80 | trailing_stop | $-83.00 |
| 19 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 20 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 21 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 22 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:35 | 3.56 | 11:37 | 3.40 | trailing_stop | $-18.00 |
| 23 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 24 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:44 | 3.63 | 11:46 | 3.98 | trailing_stop | $+33.00 |
| 25 | 2026-11-18 | SPY | long | pullback | SPY261118C00733000 | 10:00 | 3.21 | 10:01 | 3.22 | trailing_stop | $-1.00 |
| 26 | 2026-11-18 | AAPL | long | pullback | AAPL261118C00355000 | 10:00 | 1.95 | 10:01 | 1.48 | trailing_stop | $-49.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 10:10 | 2.96 | 10:14 | 2.21 | trailing_stop | $-77.00 |
| 28 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 29 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 30 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:15 | 3.71 | 10:18 | 3.23 | trailing_stop | $-50.00 |
| 31 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:20 | 3.76 | 10:23 | 3.06 | trailing_stop | $-72.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:22 | 2.49 | 10:28 | 2.38 | trailing_stop | $-13.00 |
| 33 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:24 | 2.19 | 10:34 | 1.95 | trailing_stop | $-26.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 10:30 | 3.15 | 10:39 | 3.15 | trailing_stop | $-2.00 |
| 35 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 36 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 37 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:37 | 2.66 | 10:46 | 3.17 | trailing_stop | $+49.00 |
| 38 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 39 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 10:45 | 3.94 | 10:50 | 3.59 | trailing_stop | $-37.00 |
| 40 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 41 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 42 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 43 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 44 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:17 | 2.59 | 11:21 | 2.65 | trailing_stop | $+4.00 |
| 45 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 46 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:28 | 2.70 | 11:32 | 2.24 | trailing_stop | $-48.00 |
| 47 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:31 | 3.73 | 11:32 | 3.28 | trailing_stop | $-47.00 |
| 48 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 49 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:39 | 2.66 | 11:50 | 3.34 | trailing_stop | $+66.00 |
| 50 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 51 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 52 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 53 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 54 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:49 | 3.45 | 11:50 | 2.76 | trailing_stop | $-71.00 |
| 55 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 56 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 57 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00380000 | 10:40 | 5.85 | 10:42 | 5.20 | trailing_stop | $-67.00 |
| 58 | 2026-11-19 | QQQ | short | pullback | QQQ261119P00659000 | 10:47 | 4.66 | 10:56 | 4.22 | trailing_stop | $-46.00 |
| 59 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 60 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 61 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 62 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 63 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 64 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00155000 | 11:22 | 3.85 | 11:24 | 3.65 | trailing_stop | $-22.00 |
| 65 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 66 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 67 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 68 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 69 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 70 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 71 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 72 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.50 | trailing_stop | $+288.00 |
| 73 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 11:50 | 2.55 | 11:54 | 3.40 | trailing_stop | $+83.00 |
| 74 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:31 | 2.44 | 10:34 | 1.97 | trailing_stop | $-49.00 |
| 75 | 2026-11-20 | SPY | short | pullback | SPY261120P00710000 | 10:31 | 3.82 | 10:36 | 4.03 | trailing_stop | $+19.00 |
| 76 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00631000 | 10:31 | 4.56 | 10:36 | 4.93 | trailing_stop | $+35.00 |
| 77 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00139000 | 10:31 | 1.84 | 10:39 | 2.44 | trailing_stop | $+58.00 |
| 78 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:33 | 5.15 | 10:35 | 4.45 | trailing_stop | $-72.00 |
| 79 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 80 | 2026-11-20 | SPY | short | pullback | SPY261120P00709000 | 10:43 | 3.74 | 10:48 | 4.01 | trailing_stop | $+25.00 |
| 81 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00630000 | 10:43 | 4.64 | 10:48 | 5.38 | trailing_stop | $+72.00 |
| 82 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 83 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:56 | 2.68 | 11:10 | 2.98 | trailing_stop | $+28.00 |
| 84 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 85 | 2026-11-20 | SPY | short | pullback | SPY261120P00707000 | 10:58 | 3.64 | 11:06 | 3.98 | trailing_stop | $+32.00 |
| 86 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 87 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:03 | 2.16 | 11:06 | 1.80 | trailing_stop | $-38.00 |
| 88 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 89 | 2026-11-20 | SPY | short | pullback | SPY261120P00707000 | 11:20 | 3.56 | 11:50 | 5.42 | trailing_stop | $+184.00 |
| 90 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 91 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 11:20 | 4.27 | 11:58 | 6.44 | trailing_stop | $+215.00 |
| 92 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 93 | 2026-11-23 | TSLA | long | pullback | TSLA261123C00387500 | 10:01 | 4.95 | 10:46 | 5.07 | trailing_stop | $+10.00 |
| 94 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:03 | 2.63 | 10:12 | 2.33 | trailing_stop | $-32.00 |
| 95 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:07 | 4.62 | 10:45 | 6.00 | trailing_stop | $+136.00 |
| 96 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 97 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 98 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.47 | 10:45 | 2.67 | trailing_stop | $+118.00 |
| 99 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 100 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 101 | 2026-11-23 | TSLA | long | pullback | TSLA261123C00390000 | 11:09 | 3.90 | 11:15 | 3.50 | trailing_stop | $-42.00 |
| 102 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 103 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 104 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 105 | 2026-11-23 | TSLA | long | pullback | TSLA261123C00392500 | 11:21 | 2.65 | 11:26 | 2.24 | trailing_stop | $-43.00 |
| 106 | 2026-11-23 | SPY | long | pullback | SPY261123C00725000 | 11:21 | 2.68 | 11:27 | 2.18 | trailing_stop | $-52.00 |
| 107 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:21 | 3.40 | 11:32 | 2.57 | trailing_stop | $-85.00 |
| 108 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 109 | 2026-11-23 | NVDA | short | pullback | NVDA261123P00167500 | 11:36 | 3.45 | 11:44 | 4.08 | trailing_stop | $+61.00 |
| 110 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 111 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 112 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 113 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 114 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:45 | 6.60 | 10:46 | 6.15 | trailing_stop | $-47.00 |
| 115 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 10:52 | 3.83 | 10:53 | 2.98 | trailing_stop | $-87.00 |
| 116 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 10:52 | 3.01 | 10:53 | 2.34 | trailing_stop | $-69.00 |
| 117 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 10:52 | 4.30 | 10:53 | 3.95 | trailing_stop | $-37.00 |
| 118 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 119 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 120 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 121 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:00 | 3.27 | 11:09 | 3.34 | trailing_stop | $+5.00 |
| 122 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 123 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:12 | 3.85 | 11:15 | 3.80 | trailing_stop | $-7.00 |
| 124 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:16 | 4.70 | 11:17 | 4.70 | trailing_stop | $-2.00 |
| 125 | 2026-11-24 | SPY | short | pullback | SPY261124P00713000 | 11:16 | 2.86 | 11:17 | 2.83 | trailing_stop | $-5.00 |
| 126 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00632000 | 11:16 | 3.64 | 11:17 | 3.66 | trailing_stop | $+0.00 |
| 127 | 2026-11-24 | SPY | long | pullback | SPY261124C00716000 | 11:25 | 2.74 | 11:27 | 2.55 | trailing_stop | $-21.00 |
| 128 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 129 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 130 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 131 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 132 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:41 | 4.85 | 11:44 | 4.70 | trailing_stop | $-17.00 |
| 133 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 134 | 2026-11-25 | AAPL | long | pullback | AAPL261125C00350000 | 10:02 | 2.33 | 10:04 | 1.81 | trailing_stop | $-54.00 |
| 135 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00617000 | 10:02 | 4.80 | 10:07 | 4.62 | trailing_stop | $-20.00 |
| 136 | 2026-11-25 | SPY | long | pullback | SPY261125C00703000 | 10:02 | 3.99 | 10:08 | 4.30 | trailing_stop | $+29.00 |
| 137 | 2026-11-25 | NVDA | long | pullback | NVDA261125C00145000 | 10:04 | 2.45 | 10:07 | 1.89 | trailing_stop | $-58.00 |
| 138 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00362500 | 10:04 | 4.80 | 10:15 | 4.60 | trailing_stop | $-22.00 |
| 139 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00350000 | 10:15 | 1.89 | 10:21 | 3.14 | trailing_stop | $+123.00 |
| 140 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 141 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00613000 | 10:19 | 4.39 | 10:31 | 4.54 | trailing_stop | $+13.00 |
| 142 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 143 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 144 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 10:32 | 2.67 | 10:33 | 2.82 | trailing_stop | $+13.00 |
| 145 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00614000 | 10:38 | 3.88 | 10:39 | 3.36 | trailing_stop | $-54.00 |
| 146 | 2026-11-25 | SPY | long | pullback | SPY261125C00701000 | 10:38 | 3.88 | 10:39 | 3.47 | trailing_stop | $-43.00 |
| 147 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 10:44 | 2.50 | 10:49 | 2.61 | trailing_stop | $+9.00 |
| 148 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:45 | 3.98 | 10:48 | 3.59 | trailing_stop | $-41.00 |
| 149 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 10:45 | 4.16 | 10:48 | 3.77 | trailing_stop | $-41.00 |
| 150 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:49 | 3.30 | 10:57 | 2.68 | trailing_stop | $-64.00 |
| 151 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:53 | 2.07 | 11:14 | 2.02 | trailing_stop | $-7.00 |
| 152 | 2026-11-25 | SPY | long | pullback | SPY261125C00700000 | 10:56 | 3.59 | 10:57 | 3.26 | trailing_stop | $-35.00 |
| 153 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 154 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 155 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:03 | 3.24 | 11:14 | 3.21 | trailing_stop | $-5.00 |
| 156 | 2026-11-25 | TSLA | short | pullback | TSLA261125P00362500 | 11:06 | 3.15 | 11:21 | 3.15 | trailing_stop | $-2.00 |
| 157 | 2026-11-25 | SPY | long | pullback | SPY261125C00700000 | 11:25 | 2.89 | 11:28 | 3.08 | trailing_stop | $+17.00 |
| 158 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 159 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:35 | 2.99 | 11:40 | 2.82 | trailing_stop | $-19.00 |
| 160 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:35 | 3.58 | 11:40 | 3.34 | trailing_stop | $-26.00 |

## reentry

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 120 | 34.2% | $+92.63 | $-39.18 | $+703.00 | $+5.86 | $+673.00 | $-102.00 | $+1,056.00 | $-528.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 93 | 32.3% | $+384.00 | $+4.13 |
| squeeze | 27 | 40.7% | $+319.00 | $+11.81 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| AAPL | 20 | 50.0% | $+437.00 | $+21.85 |
| QQQ | 27 | 33.3% | $+342.00 | $+12.67 |
| TSLA | 23 | 26.1% | $+33.00 | $+1.43 |
| NVDA | 27 | 40.7% | $+0.00 | $+0.00 |
| SPY | 23 | 21.7% | $-109.00 | $-4.74 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 120 | 34.2% | $+703.00 | $+5.86 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 90 | 38.9% | $+1,179.00 | $+13.10 |
| long | 30 | 20.0% | $-476.00 | $-15.87 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:50 | 2.95 | trailing_stop | $+118.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:50 | 8.49 | trailing_stop | $+133.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:50 | 7.71 | trailing_stop | $+235.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:20 | 2.85 | 11:55 | 3.19 | trailing_stop | $+32.00 |
| 11 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 12 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 13 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00652000 | 11:42 | 3.24 | 11:46 | 3.37 | trailing_stop | $+11.00 |
| 16 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:46 | 7.33 | 11:46 | 7.12 | trailing_stop | $-23.00 |
| 17 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:48 | 7.17 | 11:56 | 7.26 | trailing_stop | $+7.00 |
| 18 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00652000 | 11:48 | 3.23 | 11:56 | 3.43 | trailing_stop | $+18.00 |
| 19 | 2026-11-17 | TSLA | short | pullback | TSLA261118P00380000 | 11:48 | 6.68 | 11:56 | 6.20 | trailing_stop | $-50.00 |
| 20 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 21 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 22 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:18 | 2.48 | 10:20 | 1.88 | trailing_stop | $-62.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 25 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 26 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 27 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 28 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 29 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 30 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 32 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 34 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:28 | 3.52 | 11:32 | 3.28 | trailing_stop | $-26.00 |
| 35 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 36 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 37 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:37 | 2.39 | 11:50 | 3.34 | trailing_stop | $+93.00 |
| 38 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 39 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 40 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 41 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 42 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:44 | 3.40 | 11:50 | 2.76 | trailing_stop | $-66.00 |
| 43 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:47 | 2.57 | 11:50 | 2.25 | trailing_stop | $-34.00 |
| 44 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 45 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 46 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 47 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 48 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 50 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 51 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 52 | 2026-11-19 | SPY | long | squeeze | SPY261119C00730000 | 11:30 | 2.55 | 11:31 | 2.23 | trailing_stop | $-34.00 |
| 53 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00382500 | 11:30 | 5.25 | 11:31 | 4.70 | trailing_stop | $-57.00 |
| 54 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 55 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 56 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 57 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 58 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 59 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 60 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.50 | trailing_stop | $+288.00 |
| 61 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 62 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 63 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:52 | 2.80 | 11:10 | 2.98 | trailing_stop | $+16.00 |
| 64 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 65 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 66 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 67 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 68 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 69 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 70 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 71 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 72 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 73 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:45 | 4.30 | trailing_stop | $+152.00 |
| 74 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 75 | 2026-11-23 | TSLA | long | pullback | TSLA261123C00392500 | 10:37 | 3.55 | 10:43 | 2.85 | trailing_stop | $-72.00 |
| 76 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 77 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 78 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 79 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 80 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 81 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 82 | 2026-11-23 | SPY | long | pullback | SPY261123C00724000 | 11:20 | 3.28 | 11:27 | 2.86 | trailing_stop | $-44.00 |
| 83 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00652000 | 11:20 | 3.94 | 11:27 | 3.57 | trailing_stop | $-39.00 |
| 84 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 85 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:43 | 5.19 | trailing_stop | $+195.00 |
| 86 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 87 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:37 | 2.28 | 11:43 | 2.82 | trailing_stop | $+52.00 |
| 88 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 89 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 90 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 91 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 92 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 93 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 94 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 95 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:13 | 4.75 | 11:17 | 4.70 | trailing_stop | $-7.00 |
| 96 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00632000 | 11:13 | 3.37 | 11:20 | 3.28 | trailing_stop | $-11.00 |
| 97 | 2026-11-24 | SPY | short | pullback | SPY261124P00713000 | 11:14 | 2.89 | 11:17 | 2.83 | trailing_stop | $-8.00 |
| 98 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 99 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 100 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:36 | 4.60 | 11:44 | 4.70 | trailing_stop | $+8.00 |
| 101 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 102 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 103 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 104 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 105 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 106 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 107 | 2026-11-25 | SPY | long | pullback | SPY261125C00701000 | 10:35 | 3.70 | 10:38 | 3.46 | trailing_stop | $-26.00 |
| 108 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 109 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 110 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 111 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 112 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 113 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 114 | 2026-11-25 | AAPL | long | squeeze | AAPL261125C00347500 | 11:15 | 1.23 | 11:28 | 1.88 | trailing_stop | $+63.00 |
| 115 | 2026-11-25 | SPY | short | pullback | SPY261125P00698000 | 11:16 | 3.03 | 11:21 | 2.64 | trailing_stop | $-41.00 |
| 116 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:16 | 1.78 | 11:22 | 1.67 | trailing_stop | $-13.00 |
| 117 | 2026-11-25 | QQQ | long | squeeze | QQQ261125C00612000 | 11:23 | 3.00 | 11:29 | 3.16 | trailing_stop | $+14.00 |
| 118 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 119 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 120 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## trend

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 79 | 39.2% | $+101.48 | $-36.50 | $+1,394.00 | $+17.65 | $+673.00 | $-102.00 | $+1,147.00 | $-413.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 52 | 40.4% | $+1,152.00 | $+22.15 |
| squeeze | 27 | 37.0% | $+242.00 | $+8.96 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| QQQ | 18 | 33.3% | $+669.00 | $+37.17 |
| AAPL | 15 | 46.7% | $+371.00 | $+24.73 |
| NVDA | 17 | 52.9% | $+190.00 | $+11.18 |
| SPY | 14 | 28.6% | $+101.00 | $+7.21 |
| TSLA | 15 | 33.3% | $+63.00 | $+4.20 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 79 | 39.2% | $+1,394.00 | $+17.65 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 63 | 42.9% | $+1,304.00 | $+20.70 |
| long | 16 | 25.0% | $+90.00 | $+5.62 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 2 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:50 | 2.95 | trailing_stop | $+118.00 |
| 3 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:50 | 10.00 | trailing_stop | $+673.00 |
| 4 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:50 | 8.49 | trailing_stop | $+133.00 |
| 5 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:50 | 7.71 | trailing_stop | $+235.00 |
| 6 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:20 | 2.85 | 11:55 | 3.19 | trailing_stop | $+32.00 |
| 7 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 8 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 9 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 10 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 11 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 12 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:21 | 4.06 | 10:23 | 3.06 | trailing_stop | $-102.00 |
| 13 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 14 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 15 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 16 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 18 | 2026-11-18 | TSLA | short | squeeze | TSLA261118P00377500 | 11:17 | 1.38 | 11:22 | 1.41 | trailing_stop | $+1.00 |
| 19 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 20 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 21 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:37 | 2.39 | 11:50 | 3.34 | trailing_stop | $+93.00 |
| 22 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 24 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:47 | 2.57 | 11:50 | 2.25 | trailing_stop | $-34.00 |
| 25 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 26 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 27 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 28 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 29 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 30 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 31 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:23 | 6.20 | 11:28 | 5.40 | trailing_stop | $-82.00 |
| 32 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 33 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 34 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 35 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 36 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 37 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 38 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 39 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:43 | 2.45 | 10:49 | 2.15 | trailing_stop | $-32.00 |
| 40 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 41 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 42 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 43 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:50 | 7.22 | trailing_stop | $+335.00 |
| 44 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:25 | 1.61 | 11:50 | 1.91 | trailing_stop | $+28.00 |
| 45 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:25 | 3.10 | 11:55 | 3.65 | trailing_stop | $+53.00 |
| 46 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 47 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 48 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 49 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:45 | 4.30 | trailing_stop | $+152.00 |
| 50 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 51 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 52 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 53 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 54 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 55 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.30 | 11:33 | 2.05 | trailing_stop | $-27.00 |
| 56 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:43 | 5.19 | trailing_stop | $+195.00 |
| 57 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:43 | 4.61 | trailing_stop | $+187.00 |
| 58 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 59 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 60 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 61 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 62 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 63 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 64 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 65 | 2026-11-24 | SPY | short | pullback | SPY261124P00713000 | 11:14 | 2.89 | 11:17 | 2.83 | trailing_stop | $-8.00 |
| 66 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 67 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:36 | 4.60 | 11:44 | 4.70 | trailing_stop | $+8.00 |
| 68 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 69 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 70 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 71 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 72 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 73 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 74 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 75 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:10 | 3.41 | 11:14 | 3.21 | trailing_stop | $-22.00 |
| 76 | 2026-11-25 | QQQ | short | squeeze | QQQ261125P00609000 | 11:10 | 3.37 | 11:21 | 2.81 | trailing_stop | $-58.00 |
| 77 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:41 | 1.55 | 11:50 | 1.64 | trailing_stop | $+7.00 |
| 78 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |
| 79 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |

## ts2_10

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+80.16 | $-39.31 | $+49.00 | $+0.51 | $+266.00 | $-102.00 | $+624.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 25 | 36.0% | $+47.00 | $+1.88 |
| pullback | 71 | 32.4% | $+2.00 | $+0.03 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| SPY | 17 | 29.4% | $+174.00 | $+10.24 |
| AAPL | 17 | 35.3% | $+156.00 | $+9.18 |
| NVDA | 20 | 45.0% | $+65.00 | $+3.25 |
| TSLA | 19 | 31.6% | $-89.00 | $-4.68 |
| QQQ | 23 | 26.1% | $-257.00 | $-11.17 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| stage2_2of3 | 8 | 100.0% | $+871.00 | $+108.88 |
| stage2_trail | 4 | 100.0% | $+558.00 | $+139.50 |
| stage2_engulf | 3 | 100.0% | $+393.00 | $+131.00 |
| trailing_stop | 81 | 21.0% | $-1,773.00 | $-21.89 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+252.00 | $+3.41 |
| long | 22 | 18.2% | $-203.00 | $-9.23 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:40 | 2.25 | stage2_2of3 | $+48.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:33 | 4.69 | stage2_trail | $+142.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:33 | 7.69 | stage2_2of3 | $+53.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:41 | 6.80 | stage2_2of3 | $+144.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.39 | stage2_engulf | $+53.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.54 | stage2_2of3 | $+116.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:39 | 3.70 | stage2_2of3 | $+63.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:52 | 7.54 | stage2_trail | $+192.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:27 | 5.42 | stage2_2of3 | $+155.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:39 | 3.81 | stage2_trail | $+85.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:42 | 2.81 | stage2_engulf | $+74.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:26 | 6.51 | stage2_engulf | $+266.00 |
| 60 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:26 | 4.18 | stage2_2of3 | $+140.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:40 | 4.13 | stage2_trail | $+139.00 |
| 71 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:40 | 4.76 | stage2_2of3 | $+152.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## ts2_15

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+80.03 | $-39.31 | $+45.00 | $+0.47 | $+240.00 | $-102.00 | $+598.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 25 | 36.0% | $+66.00 | $+2.64 |
| pullback | 71 | 32.4% | $-21.00 | $-0.30 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| AAPL | 17 | 35.3% | $+156.00 | $+9.18 |
| SPY | 17 | 29.4% | $+153.00 | $+9.00 |
| NVDA | 20 | 45.0% | $+63.00 | $+3.15 |
| TSLA | 19 | 31.6% | $-70.00 | $-3.68 |
| QQQ | 23 | 26.1% | $-257.00 | $-11.17 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| stage2_trail | 9 | 100.0% | $+962.00 | $+106.89 |
| stage2_2of3 | 4 | 100.0% | $+687.00 | $+171.75 |
| stage2_engulf | 2 | 100.0% | $+169.00 | $+84.50 |
| trailing_stop | 81 | 21.0% | $-1,773.00 | $-21.89 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+274.00 | $+3.70 |
| long | 22 | 18.2% | $-229.00 | $-10.41 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:40 | 2.25 | stage2_engulf | $+48.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:33 | 4.69 | stage2_trail | $+142.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:33 | 7.65 | stage2_trail | $+49.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:42 | 6.99 | stage2_trail | $+163.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.39 | stage2_trail | $+53.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.59 | stage2_engulf | $+121.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:39 | 3.70 | stage2_trail | $+63.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:52 | 7.54 | stage2_trail | $+192.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:27 | 5.42 | stage2_2of3 | $+155.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:39 | 3.81 | stage2_trail | $+85.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:43 | 2.83 | stage2_trail | $+76.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:26 | 6.25 | stage2_2of3 | $+240.00 |
| 60 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:26 | 4.18 | stage2_2of3 | $+140.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:40 | 4.13 | stage2_trail | $+139.00 |
| 71 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:40 | 4.76 | stage2_2of3 | $+152.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## ts2_30

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+81.81 | $-39.31 | $+102.00 | $+1.06 | $+266.00 | $-102.00 | $+615.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 25 | 36.0% | $+111.00 | $+4.44 |
| pullback | 71 | 32.4% | $-9.00 | $-0.13 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| AAPL | 17 | 35.3% | $+210.00 | $+12.35 |
| SPY | 17 | 29.4% | $+165.00 | $+9.71 |
| NVDA | 20 | 45.0% | $+63.00 | $+3.15 |
| TSLA | 19 | 31.6% | $-70.00 | $-3.68 |
| QQQ | 23 | 26.1% | $-266.00 | $-11.57 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| stage2_trail | 13 | 100.0% | $+1,454.00 | $+111.85 |
| stage2_2of3 | 2 | 100.0% | $+421.00 | $+210.50 |
| trailing_stop | 81 | 21.0% | $-1,773.00 | $-21.89 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+305.00 | $+4.12 |
| long | 22 | 18.2% | $-203.00 | $-9.23 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:42 | 2.79 | stage2_trail | $+102.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:33 | 4.69 | stage2_trail | $+142.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:33 | 7.65 | stage2_trail | $+49.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:42 | 6.99 | stage2_trail | $+163.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.39 | stage2_trail | $+53.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.45 | stage2_trail | $+107.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:39 | 3.70 | stage2_trail | $+63.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:52 | 7.54 | stage2_trail | $+192.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:28 | 5.42 | stage2_2of3 | $+155.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:39 | 3.81 | stage2_trail | $+85.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:43 | 2.83 | stage2_trail | $+76.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:26 | 6.51 | stage2_2of3 | $+266.00 |
| 60 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:26 | 4.18 | stage2_trail | $+140.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:40 | 4.13 | stage2_trail | $+139.00 |
| 71 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:40 | 4.67 | stage2_trail | $+143.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## ts2_60

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+79.41 | $-39.31 | $+25.00 | $+0.26 | $+234.00 | $-102.00 | $+583.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 25 | 36.0% | $+29.00 | $+1.16 |
| pullback | 71 | 32.4% | $-4.00 | $-0.06 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| AAPL | 17 | 35.3% | $+156.00 | $+9.18 |
| SPY | 17 | 29.4% | $+133.00 | $+7.82 |
| NVDA | 20 | 45.0% | $+61.00 | $+3.05 |
| TSLA | 19 | 31.6% | $-59.00 | $-3.11 |
| QQQ | 23 | 26.1% | $-266.00 | $-11.57 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| stage2_trail | 12 | 100.0% | $+1,541.00 | $+128.42 |
| stage2_2of3 | 2 | 100.0% | $+183.00 | $+91.50 |
| stage2_engulf | 1 | 100.0% | $+74.00 | $+74.00 |
| trailing_stop | 81 | 21.0% | $-1,773.00 | $-21.89 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+260.00 | $+3.51 |
| long | 22 | 18.2% | $-235.00 | $-10.68 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:40 | 2.25 | stage2_2of3 | $+48.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:33 | 4.69 | stage2_trail | $+142.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:33 | 7.65 | stage2_trail | $+49.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:40 | 6.71 | stage2_2of3 | $+135.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.39 | stage2_trail | $+53.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.45 | stage2_trail | $+107.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:39 | 3.70 | stage2_trail | $+63.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:52 | 7.54 | stage2_trail | $+192.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:28 | 5.81 | stage2_trail | $+194.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:39 | 3.81 | stage2_trail | $+85.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:42 | 2.81 | stage2_engulf | $+74.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:27 | 6.19 | stage2_trail | $+234.00 |
| 60 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:26 | 4.18 | stage2_trail | $+140.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:40 | 4.13 | stage2_trail | $+139.00 |
| 71 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:40 | 4.67 | stage2_trail | $+143.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## ts3_10

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+102.03 | $-39.31 | $+749.00 | $+7.80 | $+469.00 | $-102.00 | $+823.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 25 | 36.0% | $+380.00 | $+15.20 |
| pullback | 71 | 32.4% | $+369.00 | $+5.20 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| AAPL | 17 | 35.3% | $+262.00 | $+15.41 |
| QQQ | 23 | 26.1% | $+180.00 | $+7.83 |
| SPY | 17 | 29.4% | $+126.00 | $+7.41 |
| NVDA | 20 | 45.0% | $+94.00 | $+4.70 |
| TSLA | 19 | 31.6% | $+87.00 | $+4.58 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| stage2_2of3 | 4 | 100.0% | $+1,020.00 | $+255.00 |
| stage2_trail | 3 | 100.0% | $+556.00 | $+185.33 |
| stage2_engulf | 2 | 100.0% | $+493.00 | $+246.50 |
| trailing_stop | 87 | 26.4% | $-1,320.00 | $-15.17 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+959.00 | $+12.96 |
| long | 22 | 18.2% | $-210.00 | $-9.55 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:42 | 2.79 | stage2_trail | $+102.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:42 | 7.96 | stage2_2of3 | $+469.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:41 | 8.27 | stage2_2of3 | $+111.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:47 | 7.53 | stage2_2of3 | $+217.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:52 | 7.54 | stage2_trail | $+192.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:32 | 6.45 | stage2_engulf | $+258.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 60 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:33 | 5.01 | stage2_2of3 | $+223.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:42 | 5.86 | stage2_trail | $+262.00 |
| 71 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:42 | 5.09 | stage2_engulf | $+235.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## ts3_15

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+96.03 | $-39.31 | $+557.00 | $+5.80 | $+271.00 | $-102.00 | $+817.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 25 | 36.0% | $+414.00 | $+16.56 |
| pullback | 71 | 32.4% | $+143.00 | $+2.01 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| AAPL | 17 | 35.3% | $+252.00 | $+14.82 |
| SPY | 17 | 29.4% | $+130.00 | $+7.65 |
| TSLA | 19 | 31.6% | $+117.00 | $+6.16 |
| NVDA | 20 | 45.0% | $+76.00 | $+3.80 |
| QQQ | 23 | 26.1% | $-18.00 | $-0.78 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| stage2_trail | 5 | 100.0% | $+1,042.00 | $+208.40 |
| stage2_2of3 | 3 | 100.0% | $+577.00 | $+192.33 |
| stage2_engulf | 1 | 100.0% | $+258.00 | $+258.00 |
| trailing_stop | 87 | 26.4% | $-1,320.00 | $-15.17 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+777.00 | $+10.50 |
| long | 22 | 18.2% | $-220.00 | $-10.00 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:42 | 2.79 | stage2_trail | $+102.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:40 | 5.98 | stage2_2of3 | $+271.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:40 | 8.09 | stage2_2of3 | $+93.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:48 | 7.83 | stage2_trail | $+247.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:52 | 7.54 | stage2_trail | $+192.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:32 | 6.45 | stage2_engulf | $+258.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 60 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:32 | 4.91 | stage2_2of3 | $+213.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:42 | 5.13 | stage2_trail | $+239.00 |
| 71 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:42 | 5.86 | stage2_trail | $+262.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## ts3_30

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+104.22 | $-39.31 | $+819.00 | $+8.53 | $+479.00 | $-102.00 | $+827.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 71 | 32.4% | $+439.00 | $+6.18 |
| squeeze | 25 | 36.0% | $+380.00 | $+15.20 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| AAPL | 17 | 35.3% | $+262.00 | $+15.41 |
| QQQ | 23 | 26.1% | $+190.00 | $+8.26 |
| TSLA | 19 | 31.6% | $+132.00 | $+6.95 |
| SPY | 17 | 29.4% | $+130.00 | $+7.65 |
| NVDA | 20 | 45.0% | $+105.00 | $+5.25 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| stage2_trail | 7 | 100.0% | $+1,804.00 | $+257.71 |
| stage2_2of3 | 2 | 100.0% | $+335.00 | $+167.50 |
| trailing_stop | 87 | 26.4% | $-1,320.00 | $-15.17 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+1,029.00 | $+13.91 |
| long | 22 | 18.2% | $-210.00 | $-9.55 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:42 | 2.79 | stage2_trail | $+102.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:42 | 8.06 | stage2_trail | $+479.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:43 | 8.38 | stage2_2of3 | $+122.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:47 | 7.49 | stage2_2of3 | $+213.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:52 | 7.54 | stage2_trail | $+192.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:33 | 6.94 | stage2_trail | $+307.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 60 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:33 | 5.01 | stage2_trail | $+223.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:42 | 5.13 | stage2_trail | $+239.00 |
| 71 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:42 | 5.86 | stage2_trail | $+262.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |

## ts3_60

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 96 | 33.3% | $+98.88 | $-39.31 | $+648.00 | $+6.75 | $+307.00 | $-102.00 | $+827.00 | $-525.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| squeeze | 25 | 36.0% | $+414.00 | $+16.56 |
| pullback | 71 | 32.4% | $+234.00 | $+3.30 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| AAPL | 17 | 35.3% | $+262.00 | $+15.41 |
| TSLA | 19 | 31.6% | $+166.00 | $+8.74 |
| SPY | 17 | 29.4% | $+130.00 | $+7.65 |
| NVDA | 20 | 45.0% | $+108.00 | $+5.40 |
| QQQ | 23 | 26.1% | $-18.00 | $-0.78 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| stage2_trail | 8 | 100.0% | $+1,697.00 | $+212.12 |
| stage2_2of3 | 1 | 100.0% | $+271.00 | $+271.00 |
| trailing_stop | 87 | 26.4% | $-1,320.00 | $-15.17 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 74 | 37.8% | $+858.00 | $+11.59 |
| long | 22 | 18.2% | $-210.00 | $-9.55 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.48 | 10:01 | 3.05 | trailing_stop | $-45.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.49 | 10:10 | 6.05 | trailing_stop | $-46.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.54 | 10:08 | 7.90 | trailing_stop | $+34.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.26 | 10:12 | 2.74 | trailing_stop | $-54.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.75 | 10:42 | 2.79 | stage2_trail | $+102.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.25 | 10:40 | 5.98 | stage2_2of3 | $+271.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.14 | 10:43 | 8.41 | stage2_trail | $+125.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.34 | 10:48 | 7.83 | stage2_trail | $+247.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 3.06 | 11:18 | 2.68 | trailing_stop | $-40.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.71 | 11:46 | 3.22 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 11:32 | 6.93 | 11:44 | 7.06 | trailing_stop | $+11.00 |
| 12 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.51 | 11:37 | 3.30 | trailing_stop | $-23.00 |
| 13 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:32 | 2.84 | 11:44 | 3.14 | trailing_stop | $+28.00 |
| 14 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.39 | 11:46 | 5.57 | trailing_stop | $+16.00 |
| 15 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.81 | 11:46 | 2.51 | trailing_stop | $-32.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.32 | 10:12 | 2.64 | trailing_stop | $-70.00 |
| 17 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.37 | 10:16 | 1.69 | trailing_stop | $-70.00 |
| 18 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.98 | 10:23 | 3.06 | trailing_stop | $-94.00 |
| 19 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.73 | 10:22 | 3.49 | trailing_stop | $-26.00 |
| 20 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.68 | trailing_stop | $+29.00 |
| 21 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.35 | 10:51 | 2.73 | trailing_stop | $+36.00 |
| 22 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.75 | 10:46 | 3.08 | trailing_stop | $+31.00 |
| 23 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:42 | 2.54 | 10:54 | 2.65 | trailing_stop | $+9.00 |
| 24 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.94 | 11:24 | 3.13 | trailing_stop | $+17.00 |
| 25 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.14 | 11:11 | 2.49 | trailing_stop | $-67.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.00 | trailing_stop | $+62.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.50 | 11:22 | 4.03 | trailing_stop | $+51.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.96 | 11:32 | 2.29 | trailing_stop | $-69.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.72 | 11:32 | 2.24 | trailing_stop | $-50.00 |
| 30 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 11:31 | 2.48 | 11:33 | 2.26 | trailing_stop | $-24.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.54 | 11:46 | 2.38 | trailing_stop | $-18.00 |
| 32 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:39 | 3.57 | 11:49 | 3.43 | trailing_stop | $-16.00 |
| 33 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.54 | trailing_stop | $-21.00 |
| 34 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.14 | 11:42 | 1.78 | trailing_stop | $-38.00 |
| 35 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.95 | 10:17 | 2.80 | trailing_stop | $-17.00 |
| 36 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:23 | 3.05 | 10:40 | 3.80 | trailing_stop | $+73.00 |
| 37 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.05 | 10:55 | 2.68 | trailing_stop | $-39.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.60 | 10:57 | 3.29 | trailing_stop | $-33.00 |
| 39 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 10:52 | 6.85 | 10:56 | 6.75 | trailing_stop | $-12.00 |
| 40 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:17 | 6.35 | 11:27 | 5.35 | trailing_stop | $-102.00 |
| 41 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.62 | trailing_stop | $-76.00 |
| 42 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00350000 | 11:30 | 2.66 | 11:31 | 2.36 | trailing_stop | $-32.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.81 | 11:31 | 3.17 | trailing_stop | $-66.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.54 | 11:43 | 1.47 | trailing_stop | $-9.00 |
| 45 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.56 | 11:43 | 2.37 | trailing_stop | $-21.00 |
| 46 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.90 | 11:43 | 1.75 | trailing_stop | $-17.00 |
| 47 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.40 | 11:43 | 4.10 | trailing_stop | $-32.00 |
| 48 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:38 | 3.63 | 11:43 | 3.40 | trailing_stop | $-25.00 |
| 49 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:52 | 7.54 | stage2_trail | $+192.00 |
| 50 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.29 | 10:49 | 2.15 | trailing_stop | $-16.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:45 | 4.55 | 10:48 | 4.30 | trailing_stop | $-27.00 |
| 52 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.58 | 11:06 | 4.66 | trailing_stop | $+6.00 |
| 53 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.90 | 11:09 | 4.35 | trailing_stop | $-57.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.18 | 11:06 | 1.80 | trailing_stop | $-40.00 |
| 55 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.85 | 11:33 | 6.94 | stage2_trail | $+307.00 |
| 56 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.94 | 11:55 | 3.65 | trailing_stop | $+69.00 |
| 57 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00138000 | 11:24 | 2.05 | 11:50 | 2.52 | trailing_stop | $+45.00 |
| 58 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.49 | 10:43 | 5.96 | trailing_stop | $+145.00 |
| 59 | 2026-11-23 | NVDA | long | pullback | NVDA261123C00165000 | 10:13 | 4.15 | 10:33 | 5.30 | trailing_stop | $+113.00 |
| 60 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.83 | 10:42 | 5.61 | trailing_stop | $+176.00 |
| 61 | 2026-11-23 | AAPL | long | pullback | AAPL261123C00347500 | 10:17 | 2.76 | 10:33 | 5.01 | stage2_trail | $+223.00 |
| 62 | 2026-11-23 | TSLA | long | squeeze | TSLA261123C00392500 | 10:20 | 2.89 | 10:34 | 2.72 | trailing_stop | $-19.00 |
| 63 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00390000 | 10:46 | 2.97 | 11:00 | 2.57 | trailing_stop | $-42.00 |
| 64 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 3.92 | 11:05 | 3.20 | trailing_stop | $-74.00 |
| 65 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:04 | 1.62 | 11:06 | 1.23 | trailing_stop | $-41.00 |
| 66 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.61 | 11:15 | 2.72 | trailing_stop | $-91.00 |
| 67 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.41 | 11:15 | 1.84 | trailing_stop | $-59.00 |
| 68 | 2026-11-23 | NVDA | short | squeeze | NVDA261123P00165000 | 11:16 | 1.55 | 11:24 | 1.69 | trailing_stop | $+12.00 |
| 69 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:26 | 2.18 | 11:33 | 2.05 | trailing_stop | $-15.00 |
| 70 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.72 | 11:42 | 5.13 | stage2_trail | $+239.00 |
| 71 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.22 | 11:42 | 5.86 | stage2_trail | $+262.00 |
| 72 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.12 | 11:43 | 1.12 | trailing_stop | $-2.00 |
| 73 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.64 | 10:45 | 4.67 | trailing_stop | $+101.00 |
| 74 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.90 | 10:45 | 5.42 | trailing_stop | $+50.00 |
| 75 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 6.65 | trailing_stop | $+33.00 |
| 76 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.62 | 11:09 | 3.48 | trailing_stop | $-16.00 |
| 77 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.15 | 11:10 | 4.15 | trailing_stop | $-2.00 |
| 78 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.40 | 11:09 | 3.34 | trailing_stop | $-8.00 |
| 79 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.61 | 11:07 | 2.32 | trailing_stop | $-31.00 |
| 80 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.25 | 11:43 | 6.00 | trailing_stop | $-27.00 |
| 81 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 82 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.61 | 11:44 | 2.38 | trailing_stop | $-25.00 |
| 83 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.30 | 11:43 | 2.91 | trailing_stop | $-41.00 |
| 84 | 2026-11-24 | AAPL | long | pullback | AAPL261125C00350000 | 11:48 | 3.95 | 11:56 | 3.50 | trailing_stop | $-47.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.84 | 10:31 | 3.76 | trailing_stop | $-10.00 |
| 86 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.76 | 10:33 | 1.82 | trailing_stop | $-96.00 |
| 87 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:26 | 2.33 | 10:33 | 1.93 | trailing_stop | $-42.00 |
| 88 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.59 | 10:39 | 3.78 | trailing_stop | $-83.00 |
| 89 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.15 | 10:57 | 2.29 | trailing_stop | $-88.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.08 | 11:14 | 1.98 | trailing_stop | $-12.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.67 | 11:14 | 3.41 | trailing_stop | $-28.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.93 | 11:21 | 3.45 | trailing_stop | $-50.00 |
| 93 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.46 | 11:12 | 2.39 | trailing_stop | $-9.00 |
| 94 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.64 | 11:51 | 1.42 | trailing_stop | $-24.00 |
| 95 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.07 | 11:45 | 2.75 | trailing_stop | $-34.00 |
| 96 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.26 | 11:45 | 2.79 | trailing_stop | $-49.00 |
