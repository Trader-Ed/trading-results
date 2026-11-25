BENCH CHECK: OK (2026-11-25 18:43, code 3182fa3, fingerprint 244339f69411)

# Version 2 variant replay: daily loss stop and profit lock (Nov 17-25, 2026)

Seven mornings (Nov 17-25, 2026) replayed through the real Version 2 engine, offline, on recorded market data, one contract per trade. A = no new entries once the day's closed P&L reaches -8% (or -10%) of start equity; open trades run on. B = once the stock moves 1x (or 1.5x) ATR in the trade's favour, the stock stop rises to entry + spread cost ((option ask - bid + $0.02) / 0.5 delta). Test-only rules; the live rulebook is unchanged.

## Comparison: P&L by day (after $2 commissions)

| Day | Live (actual) | Replay, rulebook | A -8% | A -10% | B lock 1x ATR | B lock 1.5x ATR | A-8% + B1x | A-8% + B1.5x | A-10% + B1x | A-10% + B1.5x |
|---|---|---|---|---|---|---|---|---|---|---|
| 2026-11-17 | +635 | +1,183 | +1,183 | +1,183 | +903 | +1,183 | +903 | +1,183 | +903 | +1,183 |
| 2026-11-18 | -18 | -200 | -200 | -200 | -175 | -180 | -175 | -180 | -175 | -180 |
| 2026-11-19 | -268 | +207 | +207 | +207 | +187 | +207 | +187 | +207 | +187 | +207 |
| 2026-11-20 | +338 | +483 | +483 | +483 | +450 | +483 | +450 | +483 | +450 | +483 |
| 2026-11-23 | +488 | +649 | +649 | +649 | +687 | +658 | +687 | +658 | +687 | +658 |
| 2026-11-24 | -52 | +127 | +127 | +127 | +126 | +128 | +126 | +128 | +126 | +128 |
| 2026-11-25 | -590 | -428 | -349 | -428 | -488 | -416 | -427 | -337 | -427 | -416 |
| **Total** | **+533** | **+2,021** | **+2,100** | **+2,021** | **+1,690** | **+2,063** | **+1,751** | **+2,142** | **+1,751** | **+2,063** |

The daily loss stop fired only on Nov 25 (A -8% at 11:15, A -10% at 11:46; A-8% + B1.5x and both 1x-lock combinations at 11:22; A-10% + B1.5x at 11:46). On the other six days neither limit was reached in the replay.

## Big winners

| Trade | Replay, rulebook | A -8% / -10% | B lock 1x | B lock 1.5x |
|---|---|---|---|---|
| Nov 17 QQQ short (live V1: +605) | +687 | +687 | +687 | +687 |
| Nov 17 TSLA short | +251 | +251 | +48 (locked, stopped 10:32) | +251 |
| Nov 20 TSLA short (live: +388) | +376 | +376 | +376 | +376 |
| Nov 19 TSLA short (late winner) | +302 | +302 | +302 | +302 |

## Where the replay is approximate

- Option prices: no historical option quotes exist; each quote is the contract's last trade with an estimated spread. A limit buy fills only if the contract traded at or below the limit within 5 s; market sells fill at the last trade.
- The replay differs from live even with no changes (e.g. Nov 25: -428 replay vs -590 live); compare each variant with the replay column, not the live one.
- Nov 17 and 18 were traded live by Version 1; their live column is Version 1. AMZN is watch-only on every day, as in today's rulebook.
- The lock's stock level assumes delta 0.5; theta on same-day options means a locked trade can still close slightly negative.
- Seven days, one contract: too few to choose a rule.

## Replay, rulebook

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 87 | 40.2% | $+110.63 | $-35.60 | $+2,021.00 | $+23.23 | $+687.00 | $-87.00 | $+1,183.00 | $-428.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 64 | 35.9% | $+1,322.00 | $+20.66 |
| squeeze | 23 | 52.2% | $+699.00 | $+30.39 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 40.0% | $+799.00 | $+53.27 |
| QQQ | 24 | 29.2% | $+445.00 | $+18.54 |
| AAPL | 14 | 57.1% | $+370.00 | $+26.43 |
| SPY | 18 | 33.3% | $+209.00 | $+11.61 |
| NVDA | 16 | 50.0% | $+198.00 | $+12.38 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 87 | 40.2% | $+2,021.00 | $+23.23 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 68 | 45.6% | $+2,209.00 | $+32.49 |
| long | 19 | 21.1% | $-188.00 | $-9.89 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:10 | 6.14 | trailing_stop | $-14.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:50 | 3.00 | trailing_stop | $+124.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:50 | 7.83 | trailing_stop | $+251.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.31 | trailing_stop | $-19.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:44 | 3.20 | trailing_stop | $+39.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:51 | 2.74 | trailing_stop | $+36.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.70 | trailing_stop | $+0.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:24 | 3.15 | trailing_stop | $+23.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 26 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 27 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 28 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 29 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.55 | trailing_stop | $-20.00 |
| 30 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:46 | 2.39 | trailing_stop | $-15.00 |
| 31 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 32 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 33 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:17 | 2.91 | trailing_stop | $-8.00 |
| 34 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:17 | 4.59 | trailing_stop | $+130.00 |
| 35 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 36 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 37 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:57 | 3.20 | trailing_stop | $-51.00 |
| 38 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 39 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 40 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 41 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.40 | trailing_stop | $-22.00 |
| 42 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:43 | 3.50 | trailing_stop | $-29.00 |
| 43 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:43 | 1.55 | trailing_stop | $+4.00 |
| 45 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 46 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 47 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:49 | 2.29 | trailing_stop | $-5.00 |
| 48 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 49 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:09 | 4.53 | trailing_stop | $-26.00 |
| 50 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 52 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:55 | 4.20 | trailing_stop | $+126.00 |
| 53 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 54 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 55 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 56 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 57 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 11:00 | 0.15 | trailing_stop | $-7.00 |
| 58 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 59 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 60 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 61 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:33 | 2.13 | trailing_stop | $-11.00 |
| 62 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 63 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 64 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.10 | 11:43 | 1.16 | trailing_stop | $+4.00 |
| 65 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 66 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 67 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 68 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 69 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:10 | 4.17 | trailing_stop | $+2.00 |
| 70 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:09 | 3.35 | trailing_stop | $-8.00 |
| 71 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 72 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:43 | 6.10 | trailing_stop | $-5.00 |
| 73 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 74 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:44 | 2.42 | trailing_stop | $-26.00 |
| 75 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 76 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:31 | 3.65 | trailing_stop | $-25.00 |
| 77 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 78 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 79 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 80 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 81 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 82 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:14 | 3.42 | trailing_stop | $-30.00 |
| 83 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:21 | 3.50 | trailing_stop | $-44.00 |
| 84 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:12 | 2.54 | trailing_stop | $+5.00 |
| 85 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.65 | 11:51 | 1.45 | trailing_stop | $-22.00 |
| 86 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.06 | 11:45 | 2.81 | trailing_stop | $-27.00 |
| 87 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.27 | 11:45 | 2.99 | trailing_stop | $-30.00 |

## A -8%

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 84 | 41.7% | $+110.63 | $-36.16 | $+2,100.00 | $+25.00 | $+687.00 | $-87.00 | $+1,183.00 | $-349.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 61 | 37.7% | $+1,401.00 | $+22.97 |
| squeeze | 23 | 52.2% | $+699.00 | $+30.39 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 40.0% | $+799.00 | $+53.27 |
| QQQ | 23 | 30.4% | $+475.00 | $+20.65 |
| AAPL | 14 | 57.1% | $+370.00 | $+26.43 |
| SPY | 17 | 35.3% | $+236.00 | $+13.88 |
| NVDA | 15 | 53.3% | $+220.00 | $+14.67 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 84 | 41.7% | $+2,100.00 | $+25.00 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 65 | 47.7% | $+2,288.00 | $+35.20 |
| long | 19 | 21.1% | $-188.00 | $-9.89 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:10 | 6.14 | trailing_stop | $-14.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:50 | 3.00 | trailing_stop | $+124.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:50 | 7.83 | trailing_stop | $+251.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.31 | trailing_stop | $-19.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:44 | 3.20 | trailing_stop | $+39.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:51 | 2.74 | trailing_stop | $+36.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.70 | trailing_stop | $+0.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:24 | 3.15 | trailing_stop | $+23.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 26 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 27 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 28 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 29 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.55 | trailing_stop | $-20.00 |
| 30 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:46 | 2.39 | trailing_stop | $-15.00 |
| 31 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 32 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 33 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:17 | 2.91 | trailing_stop | $-8.00 |
| 34 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:17 | 4.59 | trailing_stop | $+130.00 |
| 35 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 36 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 37 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:57 | 3.20 | trailing_stop | $-51.00 |
| 38 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 39 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 40 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 41 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.40 | trailing_stop | $-22.00 |
| 42 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:43 | 3.50 | trailing_stop | $-29.00 |
| 43 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:43 | 1.55 | trailing_stop | $+4.00 |
| 45 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 46 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 47 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:49 | 2.29 | trailing_stop | $-5.00 |
| 48 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 49 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:09 | 4.53 | trailing_stop | $-26.00 |
| 50 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 52 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:55 | 4.20 | trailing_stop | $+126.00 |
| 53 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 54 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 55 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 56 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 57 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 11:00 | 0.15 | trailing_stop | $-7.00 |
| 58 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 59 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 60 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 61 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:33 | 2.13 | trailing_stop | $-11.00 |
| 62 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 63 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 64 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.10 | 11:43 | 1.16 | trailing_stop | $+4.00 |
| 65 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 66 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 67 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 68 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 69 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:10 | 4.17 | trailing_stop | $+2.00 |
| 70 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:09 | 3.35 | trailing_stop | $-8.00 |
| 71 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 72 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:43 | 6.10 | trailing_stop | $-5.00 |
| 73 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 74 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:44 | 2.42 | trailing_stop | $-26.00 |
| 75 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 76 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:31 | 3.65 | trailing_stop | $-25.00 |
| 77 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 78 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 79 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 80 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 81 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 82 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:14 | 3.42 | trailing_stop | $-30.00 |
| 83 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:21 | 3.50 | trailing_stop | $-44.00 |
| 84 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:12 | 2.54 | trailing_stop | $+5.00 |

## A -10%

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 87 | 40.2% | $+110.63 | $-35.60 | $+2,021.00 | $+23.23 | $+687.00 | $-87.00 | $+1,183.00 | $-428.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 64 | 35.9% | $+1,322.00 | $+20.66 |
| squeeze | 23 | 52.2% | $+699.00 | $+30.39 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 40.0% | $+799.00 | $+53.27 |
| QQQ | 24 | 29.2% | $+445.00 | $+18.54 |
| AAPL | 14 | 57.1% | $+370.00 | $+26.43 |
| SPY | 18 | 33.3% | $+209.00 | $+11.61 |
| NVDA | 16 | 50.0% | $+198.00 | $+12.38 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 87 | 40.2% | $+2,021.00 | $+23.23 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 68 | 45.6% | $+2,209.00 | $+32.49 |
| long | 19 | 21.1% | $-188.00 | $-9.89 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:10 | 6.14 | trailing_stop | $-14.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:50 | 3.00 | trailing_stop | $+124.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:50 | 7.83 | trailing_stop | $+251.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.31 | trailing_stop | $-19.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:44 | 3.20 | trailing_stop | $+39.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:51 | 2.74 | trailing_stop | $+36.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.70 | trailing_stop | $+0.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:24 | 3.15 | trailing_stop | $+23.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 26 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 27 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 28 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 29 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.55 | trailing_stop | $-20.00 |
| 30 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:46 | 2.39 | trailing_stop | $-15.00 |
| 31 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 32 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 33 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:17 | 2.91 | trailing_stop | $-8.00 |
| 34 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:17 | 4.59 | trailing_stop | $+130.00 |
| 35 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 36 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 37 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:57 | 3.20 | trailing_stop | $-51.00 |
| 38 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 39 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 40 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 41 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.40 | trailing_stop | $-22.00 |
| 42 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:43 | 3.50 | trailing_stop | $-29.00 |
| 43 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:43 | 1.55 | trailing_stop | $+4.00 |
| 45 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 46 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 47 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:49 | 2.29 | trailing_stop | $-5.00 |
| 48 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 49 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:09 | 4.53 | trailing_stop | $-26.00 |
| 50 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 52 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:55 | 4.20 | trailing_stop | $+126.00 |
| 53 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 54 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 55 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 56 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 57 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 11:00 | 0.15 | trailing_stop | $-7.00 |
| 58 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 59 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 60 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 61 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:33 | 2.13 | trailing_stop | $-11.00 |
| 62 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 63 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 64 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.10 | 11:43 | 1.16 | trailing_stop | $+4.00 |
| 65 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 66 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 67 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 68 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 69 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:10 | 4.17 | trailing_stop | $+2.00 |
| 70 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:09 | 3.35 | trailing_stop | $-8.00 |
| 71 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 72 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:43 | 6.10 | trailing_stop | $-5.00 |
| 73 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 74 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:44 | 2.42 | trailing_stop | $-26.00 |
| 75 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 76 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:31 | 3.65 | trailing_stop | $-25.00 |
| 77 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 78 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 79 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 80 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 81 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 82 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:14 | 3.42 | trailing_stop | $-30.00 |
| 83 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:21 | 3.50 | trailing_stop | $-44.00 |
| 84 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:12 | 2.54 | trailing_stop | $+5.00 |
| 85 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.65 | 11:51 | 1.45 | trailing_stop | $-22.00 |
| 86 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.06 | 11:45 | 2.81 | trailing_stop | $-27.00 |
| 87 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.27 | 11:45 | 2.99 | trailing_stop | $-30.00 |

## B lock 1x ATR

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 92 | 51.1% | $+73.19 | $-38.89 | $+1,690.00 | $+18.37 | $+687.00 | $-87.00 | $+903.00 | $-488.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 69 | 49.3% | $+1,290.00 | $+18.70 |
| squeeze | 23 | 56.5% | $+400.00 | $+17.39 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 66.7% | $+729.00 | $+48.60 |
| QQQ | 25 | 32.0% | $+449.00 | $+17.96 |
| AAPL | 14 | 85.7% | $+217.00 | $+15.50 |
| NVDA | 17 | 52.9% | $+209.00 | $+12.29 |
| SPY | 21 | 38.1% | $+86.00 | $+4.10 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 92 | 51.1% | $+1,690.00 | $+18.37 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 72 | 56.9% | $+1,790.00 | $+24.86 |
| long | 20 | 30.0% | $-100.00 | $-5.00 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:09 | 6.54 | trailing_stop | $+26.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:32 | 1.83 | trailing_stop | $+7.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:32 | 5.80 | trailing_stop | $+48.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.50 | trailing_stop | $+0.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:36 | 3.01 | trailing_stop | $+20.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:36 | 2.47 | trailing_stop | $+9.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.90 | trailing_stop | $+20.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:03 | 2.99 | trailing_stop | $+7.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:13 | 3.20 | 11:23 | 3.30 | trailing_stop | $+8.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 30 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:45 | 2.77 | trailing_stop | $+2.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:45 | 2.57 | trailing_stop | $+3.00 |
| 32 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 33 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 34 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:16 | 3.08 | trailing_stop | $+9.00 |
| 35 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:11 | 3.42 | trailing_stop | $+13.00 |
| 36 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 37 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:50 | 3.65 | trailing_stop | $-6.00 |
| 39 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 40 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 41 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 42 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.57 | trailing_stop | $-5.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:42 | 3.68 | trailing_stop | $-11.00 |
| 44 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 45 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:42 | 1.55 | trailing_stop | $+4.00 |
| 46 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 47 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 48 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:48 | 2.41 | trailing_stop | $+7.00 |
| 49 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 50 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:04 | 5.15 | trailing_stop | $+36.00 |
| 51 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 52 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 53 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:26 | 3.13 | trailing_stop | $+19.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 55 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 56 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 57 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 58 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 10:56 | 0.24 | trailing_stop | $+2.00 |
| 59 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 60 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 61 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 62 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:28 | 2.38 | trailing_stop | $+14.00 |
| 63 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 64 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 65 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:38 | 1.16 | 11:42 | 1.26 | trailing_stop | $+8.00 |
| 66 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 67 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 68 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 69 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 70 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:08 | 4.18 | trailing_stop | $+3.00 |
| 71 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:03 | 3.38 | trailing_stop | $-5.00 |
| 72 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 73 | 2026-11-24 | SPY | short | pullback | SPY261124P00713000 | 11:14 | 2.86 | 11:17 | 2.37 | trailing_stop | $-51.00 |
| 74 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:37 | 6.32 | trailing_stop | $+17.00 |
| 75 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 76 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:42 | 2.66 | trailing_stop | $-2.00 |
| 77 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 78 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:21 | 3.74 | trailing_stop | $-16.00 |
| 79 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 80 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 81 | 2026-11-25 | SPY | long | pullback | SPY261125C00701000 | 10:35 | 3.74 | 10:37 | 3.89 | trailing_stop | $+13.00 |
| 82 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 83 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 84 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:11 | 3.54 | trailing_stop | $-18.00 |
| 86 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:11 | 3.77 | trailing_stop | $-17.00 |
| 87 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:11 | 2.66 | trailing_stop | $+17.00 |
| 88 | 2026-11-25 | SPY | short | pullback | SPY261125P00698000 | 11:18 | 3.14 | 11:21 | 2.47 | trailing_stop | $-69.00 |
| 89 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00609000 | 11:18 | 3.39 | 11:21 | 2.59 | trailing_stop | $-82.00 |
| 90 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.65 | 11:45 | 1.63 | trailing_stop | $-4.00 |
| 91 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.06 | 11:45 | 2.81 | trailing_stop | $-27.00 |
| 92 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.27 | 11:45 | 2.99 | trailing_stop | $-30.00 |

## B lock 1.5x ATR

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 87 | 42.5% | $+105.59 | $-36.88 | $+2,063.00 | $+23.71 | $+687.00 | $-87.00 | $+1,183.00 | $-416.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 64 | 37.5% | $+1,355.00 | $+21.17 |
| squeeze | 23 | 56.5% | $+708.00 | $+30.78 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 46.7% | $+808.00 | $+53.87 |
| QQQ | 24 | 29.2% | $+445.00 | $+18.54 |
| AAPL | 14 | 64.3% | $+402.00 | $+28.71 |
| SPY | 18 | 33.3% | $+209.00 | $+11.61 |
| NVDA | 16 | 50.0% | $+199.00 | $+12.44 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 87 | 42.5% | $+2,063.00 | $+23.71 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 68 | 48.5% | $+2,251.00 | $+33.10 |
| long | 19 | 21.1% | $-188.00 | $-9.89 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:10 | 6.14 | trailing_stop | $-14.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:50 | 3.00 | trailing_stop | $+124.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:50 | 7.83 | trailing_stop | $+251.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.31 | trailing_stop | $-19.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:44 | 3.20 | trailing_stop | $+39.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:51 | 2.74 | trailing_stop | $+36.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.90 | trailing_stop | $+20.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:24 | 3.15 | trailing_stop | $+23.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 26 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 27 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 28 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 29 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.55 | trailing_stop | $-20.00 |
| 30 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:46 | 2.39 | trailing_stop | $-15.00 |
| 31 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 32 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 33 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:17 | 2.91 | trailing_stop | $-8.00 |
| 34 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:17 | 4.59 | trailing_stop | $+130.00 |
| 35 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 36 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 37 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:57 | 3.20 | trailing_stop | $-51.00 |
| 38 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 39 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 40 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 41 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.40 | trailing_stop | $-22.00 |
| 42 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:43 | 3.50 | trailing_stop | $-29.00 |
| 43 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:43 | 1.55 | trailing_stop | $+4.00 |
| 45 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 46 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 47 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:49 | 2.29 | trailing_stop | $-5.00 |
| 48 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 49 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:09 | 4.53 | trailing_stop | $-26.00 |
| 50 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 52 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:55 | 4.20 | trailing_stop | $+126.00 |
| 53 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 54 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 55 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 56 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 57 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 10:56 | 0.24 | trailing_stop | $+2.00 |
| 58 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 59 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 60 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 61 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:33 | 2.13 | trailing_stop | $-11.00 |
| 62 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 63 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 64 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.10 | 11:43 | 1.16 | trailing_stop | $+4.00 |
| 65 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 66 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 67 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 68 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 69 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:08 | 4.18 | trailing_stop | $+3.00 |
| 70 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:09 | 3.35 | trailing_stop | $-8.00 |
| 71 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 72 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:43 | 6.10 | trailing_stop | $-5.00 |
| 73 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 74 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:44 | 2.42 | trailing_stop | $-26.00 |
| 75 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 76 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:31 | 3.65 | trailing_stop | $-25.00 |
| 77 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 78 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 79 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 80 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 81 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 82 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:14 | 3.42 | trailing_stop | $-30.00 |
| 83 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:21 | 3.50 | trailing_stop | $-44.00 |
| 84 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:11 | 2.66 | trailing_stop | $+17.00 |
| 85 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.65 | 11:51 | 1.45 | trailing_stop | $-22.00 |
| 86 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.06 | 11:45 | 2.81 | trailing_stop | $-27.00 |
| 87 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.27 | 11:45 | 2.99 | trailing_stop | $-30.00 |

## A-8% + B1x

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 89 | 52.8% | $+73.19 | $-40.21 | $+1,751.00 | $+19.67 | $+687.00 | $-87.00 | $+903.00 | $-427.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 66 | 51.5% | $+1,351.00 | $+20.47 |
| squeeze | 23 | 56.5% | $+400.00 | $+17.39 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 66.7% | $+729.00 | $+48.60 |
| QQQ | 24 | 33.3% | $+479.00 | $+19.96 |
| AAPL | 14 | 85.7% | $+217.00 | $+15.50 |
| NVDA | 16 | 56.2% | $+213.00 | $+13.31 |
| SPY | 20 | 40.0% | $+113.00 | $+5.65 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 89 | 52.8% | $+1,751.00 | $+19.67 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 69 | 59.4% | $+1,851.00 | $+26.83 |
| long | 20 | 30.0% | $-100.00 | $-5.00 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:09 | 6.54 | trailing_stop | $+26.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:32 | 1.83 | trailing_stop | $+7.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:32 | 5.80 | trailing_stop | $+48.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.50 | trailing_stop | $+0.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:36 | 3.01 | trailing_stop | $+20.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:36 | 2.47 | trailing_stop | $+9.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.90 | trailing_stop | $+20.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:03 | 2.99 | trailing_stop | $+7.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:13 | 3.20 | 11:23 | 3.30 | trailing_stop | $+8.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 30 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:45 | 2.77 | trailing_stop | $+2.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:45 | 2.57 | trailing_stop | $+3.00 |
| 32 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 33 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 34 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:16 | 3.08 | trailing_stop | $+9.00 |
| 35 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:11 | 3.42 | trailing_stop | $+13.00 |
| 36 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 37 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:50 | 3.65 | trailing_stop | $-6.00 |
| 39 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 40 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 41 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 42 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.57 | trailing_stop | $-5.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:42 | 3.68 | trailing_stop | $-11.00 |
| 44 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 45 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:42 | 1.55 | trailing_stop | $+4.00 |
| 46 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 47 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 48 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:48 | 2.41 | trailing_stop | $+7.00 |
| 49 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 50 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:04 | 5.15 | trailing_stop | $+36.00 |
| 51 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 52 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 53 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:26 | 3.13 | trailing_stop | $+19.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 55 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 56 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 57 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 58 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 10:56 | 0.24 | trailing_stop | $+2.00 |
| 59 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 60 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 61 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 62 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:28 | 2.38 | trailing_stop | $+14.00 |
| 63 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 64 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 65 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:38 | 1.16 | 11:42 | 1.26 | trailing_stop | $+8.00 |
| 66 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 67 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 68 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 69 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 70 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:08 | 4.18 | trailing_stop | $+3.00 |
| 71 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:03 | 3.38 | trailing_stop | $-5.00 |
| 72 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 73 | 2026-11-24 | SPY | short | pullback | SPY261124P00713000 | 11:14 | 2.86 | 11:17 | 2.37 | trailing_stop | $-51.00 |
| 74 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:37 | 6.32 | trailing_stop | $+17.00 |
| 75 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 76 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:42 | 2.66 | trailing_stop | $-2.00 |
| 77 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 78 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:21 | 3.74 | trailing_stop | $-16.00 |
| 79 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 80 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 81 | 2026-11-25 | SPY | long | pullback | SPY261125C00701000 | 10:35 | 3.74 | 10:37 | 3.89 | trailing_stop | $+13.00 |
| 82 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 83 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 84 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:11 | 3.54 | trailing_stop | $-18.00 |
| 86 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:11 | 3.77 | trailing_stop | $-17.00 |
| 87 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:11 | 2.66 | trailing_stop | $+17.00 |
| 88 | 2026-11-25 | SPY | short | pullback | SPY261125P00698000 | 11:18 | 3.14 | 11:21 | 2.47 | trailing_stop | $-69.00 |
| 89 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00609000 | 11:18 | 3.39 | 11:21 | 2.59 | trailing_stop | $-82.00 |

## A-8% + B1.5x

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 84 | 44.0% | $+105.59 | $-37.55 | $+2,142.00 | $+25.50 | $+687.00 | $-87.00 | $+1,183.00 | $-337.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 61 | 39.3% | $+1,434.00 | $+23.51 |
| squeeze | 23 | 56.5% | $+708.00 | $+30.78 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 46.7% | $+808.00 | $+53.87 |
| QQQ | 23 | 30.4% | $+475.00 | $+20.65 |
| AAPL | 14 | 64.3% | $+402.00 | $+28.71 |
| SPY | 17 | 35.3% | $+236.00 | $+13.88 |
| NVDA | 15 | 53.3% | $+221.00 | $+14.73 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 84 | 44.0% | $+2,142.00 | $+25.50 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 65 | 50.8% | $+2,330.00 | $+35.85 |
| long | 19 | 21.1% | $-188.00 | $-9.89 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:10 | 6.14 | trailing_stop | $-14.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:50 | 3.00 | trailing_stop | $+124.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:50 | 7.83 | trailing_stop | $+251.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.31 | trailing_stop | $-19.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:44 | 3.20 | trailing_stop | $+39.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:51 | 2.74 | trailing_stop | $+36.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.90 | trailing_stop | $+20.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:24 | 3.15 | trailing_stop | $+23.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 26 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 27 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 28 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 29 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.55 | trailing_stop | $-20.00 |
| 30 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:46 | 2.39 | trailing_stop | $-15.00 |
| 31 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 32 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 33 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:17 | 2.91 | trailing_stop | $-8.00 |
| 34 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:17 | 4.59 | trailing_stop | $+130.00 |
| 35 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 36 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 37 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:57 | 3.20 | trailing_stop | $-51.00 |
| 38 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 39 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 40 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 41 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.40 | trailing_stop | $-22.00 |
| 42 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:43 | 3.50 | trailing_stop | $-29.00 |
| 43 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:43 | 1.55 | trailing_stop | $+4.00 |
| 45 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 46 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 47 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:49 | 2.29 | trailing_stop | $-5.00 |
| 48 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 49 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:09 | 4.53 | trailing_stop | $-26.00 |
| 50 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 52 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:55 | 4.20 | trailing_stop | $+126.00 |
| 53 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 54 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 55 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 56 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 57 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 10:56 | 0.24 | trailing_stop | $+2.00 |
| 58 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 59 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 60 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 61 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:33 | 2.13 | trailing_stop | $-11.00 |
| 62 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 63 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 64 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.10 | 11:43 | 1.16 | trailing_stop | $+4.00 |
| 65 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 66 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 67 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 68 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 69 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:08 | 4.18 | trailing_stop | $+3.00 |
| 70 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:09 | 3.35 | trailing_stop | $-8.00 |
| 71 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 72 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:43 | 6.10 | trailing_stop | $-5.00 |
| 73 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 74 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:44 | 2.42 | trailing_stop | $-26.00 |
| 75 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 76 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:31 | 3.65 | trailing_stop | $-25.00 |
| 77 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 78 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 79 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 80 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 81 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 82 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:14 | 3.42 | trailing_stop | $-30.00 |
| 83 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:21 | 3.50 | trailing_stop | $-44.00 |
| 84 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:11 | 2.66 | trailing_stop | $+17.00 |

## A-10% + B1x

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 89 | 52.8% | $+73.19 | $-40.21 | $+1,751.00 | $+19.67 | $+687.00 | $-87.00 | $+903.00 | $-427.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 66 | 51.5% | $+1,351.00 | $+20.47 |
| squeeze | 23 | 56.5% | $+400.00 | $+17.39 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 66.7% | $+729.00 | $+48.60 |
| QQQ | 24 | 33.3% | $+479.00 | $+19.96 |
| AAPL | 14 | 85.7% | $+217.00 | $+15.50 |
| NVDA | 16 | 56.2% | $+213.00 | $+13.31 |
| SPY | 20 | 40.0% | $+113.00 | $+5.65 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 89 | 52.8% | $+1,751.00 | $+19.67 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 69 | 59.4% | $+1,851.00 | $+26.83 |
| long | 20 | 30.0% | $-100.00 | $-5.00 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:09 | 6.54 | trailing_stop | $+26.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:32 | 1.83 | trailing_stop | $+7.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:32 | 5.80 | trailing_stop | $+48.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.50 | trailing_stop | $+0.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:36 | 3.01 | trailing_stop | $+20.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:36 | 2.47 | trailing_stop | $+9.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.90 | trailing_stop | $+20.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:03 | 2.99 | trailing_stop | $+7.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 11:13 | 3.20 | 11:23 | 3.30 | trailing_stop | $+8.00 |
| 26 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 27 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 28 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 29 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 30 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:45 | 2.77 | trailing_stop | $+2.00 |
| 31 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:45 | 2.57 | trailing_stop | $+3.00 |
| 32 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 33 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 34 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:16 | 3.08 | trailing_stop | $+9.00 |
| 35 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:11 | 3.42 | trailing_stop | $+13.00 |
| 36 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 37 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 38 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:50 | 3.65 | trailing_stop | $-6.00 |
| 39 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 40 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 41 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 42 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.57 | trailing_stop | $-5.00 |
| 43 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:42 | 3.68 | trailing_stop | $-11.00 |
| 44 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 45 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:42 | 1.55 | trailing_stop | $+4.00 |
| 46 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 47 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 48 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:48 | 2.41 | trailing_stop | $+7.00 |
| 49 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 50 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:04 | 5.15 | trailing_stop | $+36.00 |
| 51 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 52 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 53 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:26 | 3.13 | trailing_stop | $+19.00 |
| 54 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 55 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 56 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 57 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 58 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 10:56 | 0.24 | trailing_stop | $+2.00 |
| 59 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 60 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 61 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 62 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:28 | 2.38 | trailing_stop | $+14.00 |
| 63 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 64 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 65 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:38 | 1.16 | 11:42 | 1.26 | trailing_stop | $+8.00 |
| 66 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 67 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 68 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 69 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 70 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:08 | 4.18 | trailing_stop | $+3.00 |
| 71 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:03 | 3.38 | trailing_stop | $-5.00 |
| 72 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 73 | 2026-11-24 | SPY | short | pullback | SPY261124P00713000 | 11:14 | 2.86 | 11:17 | 2.37 | trailing_stop | $-51.00 |
| 74 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:37 | 6.32 | trailing_stop | $+17.00 |
| 75 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 76 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:42 | 2.66 | trailing_stop | $-2.00 |
| 77 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 78 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:21 | 3.74 | trailing_stop | $-16.00 |
| 79 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 80 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 81 | 2026-11-25 | SPY | long | pullback | SPY261125C00701000 | 10:35 | 3.74 | 10:37 | 3.89 | trailing_stop | $+13.00 |
| 82 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 83 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 84 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 85 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:11 | 3.54 | trailing_stop | $-18.00 |
| 86 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:11 | 3.77 | trailing_stop | $-17.00 |
| 87 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:11 | 2.66 | trailing_stop | $+17.00 |
| 88 | 2026-11-25 | SPY | short | pullback | SPY261125P00698000 | 11:18 | 3.14 | 11:21 | 2.47 | trailing_stop | $-69.00 |
| 89 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00609000 | 11:18 | 3.39 | 11:21 | 2.59 | trailing_stop | $-82.00 |

## A-10% + B1.5x

### Summary

| Trades | Win rate | Avg win | Avg loss | Total P&L | P&L/trade | Best trade | Worst trade | Best day | Worst day |
|---|---|---|---|---|---|---|---|---|---|
| 87 | 42.5% | $+105.59 | $-36.88 | $+2,063.00 | $+23.71 | $+687.00 | $-87.00 | $+1,183.00 | $-416.00 |

### By setup

| Setup | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| pullback | 64 | 37.5% | $+1,355.00 | $+21.17 |
| squeeze | 23 | 56.5% | $+708.00 | $+30.78 |

### By underlying

| Underlying | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| TSLA | 15 | 46.7% | $+808.00 | $+53.87 |
| QQQ | 24 | 29.2% | $+445.00 | $+18.54 |
| AAPL | 14 | 64.3% | $+402.00 | $+28.71 |
| SPY | 18 | 33.3% | $+209.00 | $+11.61 |
| NVDA | 16 | 50.0% | $+199.00 | $+12.44 |

### By exit reason

| Exit reason | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| trailing_stop | 87 | 42.5% | $+2,063.00 | $+23.71 |

### By side

| Side | Trades | Win rate | Total P&L | P&L/trade |
|---|---|---|---|---|
| short | 68 | 48.5% | $+2,251.00 | $+33.10 |
| long | 19 | 21.1% | $-188.00 | $-9.89 |

### Trades

| # | Day | Und | Side | Setup | Contract | Entry | Entry px | Exit | Exit px | Reason | P&L |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-17 | QQQ | long | pullback | QQQ261117C00662000 | 10:00 | 3.47 | 10:01 | 3.06 | trailing_stop | $-43.00 |
| 2 | 2026-11-17 | TSLA | long | pullback | TSLA261118C00380000 | 10:00 | 6.26 | 10:10 | 6.14 | trailing_stop | $-14.00 |
| 3 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00157500 | 10:03 | 7.50 | 10:08 | 7.95 | trailing_stop | $+43.00 |
| 4 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00659000 | 10:10 | 3.24 | 10:12 | 2.75 | trailing_stop | $-51.00 |
| 5 | 2026-11-17 | AAPL | short | squeeze | AAPL261118P00352500 | 10:21 | 1.74 | 10:50 | 3.00 | trailing_stop | $+124.00 |
| 6 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00659000 | 10:29 | 3.22 | 10:50 | 10.11 | trailing_stop | $+687.00 |
| 7 | 2026-11-17 | NVDA | short | pullback | NVDA261118P00155000 | 10:30 | 7.09 | 10:50 | 8.56 | trailing_stop | $+145.00 |
| 8 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00380000 | 10:31 | 5.30 | 10:50 | 7.83 | trailing_stop | $+251.00 |
| 9 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:17 | 2.98 | 11:18 | 2.73 | trailing_stop | $-27.00 |
| 10 | 2026-11-17 | SPY | short | squeeze | SPY261117P00731000 | 11:23 | 2.72 | 11:46 | 3.23 | trailing_stop | $+49.00 |
| 11 | 2026-11-17 | QQQ | short | pullback | QQQ261117P00653000 | 11:32 | 3.48 | 11:37 | 3.31 | trailing_stop | $-19.00 |
| 12 | 2026-11-17 | AAPL | short | pullback | AAPL261118P00352500 | 11:33 | 2.79 | 11:44 | 3.20 | trailing_stop | $+39.00 |
| 13 | 2026-11-17 | TSLA | short | squeeze | TSLA261118P00377500 | 11:36 | 5.35 | 11:46 | 5.66 | trailing_stop | $+29.00 |
| 14 | 2026-11-17 | QQQ | short | squeeze | QQQ261117P00650000 | 11:46 | 2.80 | 11:46 | 2.52 | trailing_stop | $-30.00 |
| 15 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:11 | 2.35 | 10:16 | 1.70 | trailing_stop | $-67.00 |
| 16 | 2026-11-18 | SPY | short | pullback | SPY261118P00732000 | 10:11 | 3.30 | 10:12 | 2.65 | trailing_stop | $-67.00 |
| 17 | 2026-11-18 | TSLA | long | pullback | TSLA261118C00382500 | 10:15 | 3.85 | 10:23 | 3.11 | trailing_stop | $-76.00 |
| 18 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00660000 | 10:20 | 3.69 | 10:22 | 3.50 | trailing_stop | $-21.00 |
| 19 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:32 | 2.74 | 10:46 | 3.10 | trailing_stop | $+34.00 |
| 20 | 2026-11-18 | SPY | short | squeeze | SPY261118P00730000 | 10:32 | 2.36 | 10:51 | 2.74 | trailing_stop | $+36.00 |
| 21 | 2026-11-18 | QQQ | short | squeeze | QQQ261118P00658000 | 10:32 | 3.37 | 10:51 | 3.70 | trailing_stop | $+31.00 |
| 22 | 2026-11-18 | AAPL | short | pullback | AAPL261118P00355000 | 10:43 | 2.68 | 10:54 | 2.90 | trailing_stop | $+20.00 |
| 23 | 2026-11-18 | NVDA | short | pullback | NVDA261118P00155000 | 10:55 | 2.90 | 11:24 | 3.15 | trailing_stop | $+23.00 |
| 24 | 2026-11-18 | QQQ | long | pullback | QQQ261118C00658000 | 11:06 | 3.12 | 11:11 | 2.50 | trailing_stop | $-64.00 |
| 25 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:13 | 2.36 | 11:21 | 3.01 | trailing_stop | $+63.00 |
| 26 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00382500 | 11:14 | 3.20 | 11:22 | 4.09 | trailing_stop | $+87.00 |
| 27 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:28 | 2.92 | 11:32 | 2.30 | trailing_stop | $-64.00 |
| 28 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:31 | 2.71 | 11:32 | 2.25 | trailing_stop | $-48.00 |
| 29 | 2026-11-18 | QQQ | short | pullback | QQQ261118P00655000 | 11:39 | 2.73 | 11:46 | 2.55 | trailing_stop | $-20.00 |
| 30 | 2026-11-18 | SPY | short | pullback | SPY261118P00729000 | 11:39 | 2.52 | 11:46 | 2.39 | trailing_stop | $-15.00 |
| 31 | 2026-11-18 | TSLA | short | pullback | TSLA261118P00380000 | 11:40 | 2.10 | 11:42 | 1.80 | trailing_stop | $-32.00 |
| 32 | 2026-11-19 | QQQ | long | pullback | QQQ261119C00673000 | 10:05 | 3.87 | 10:09 | 3.24 | trailing_stop | $-65.00 |
| 33 | 2026-11-19 | AAPL | short | pullback | AAPL261120P00350000 | 10:08 | 2.97 | 10:17 | 2.91 | trailing_stop | $-8.00 |
| 34 | 2026-11-19 | SPY | short | pullback | SPY261119P00737000 | 10:10 | 3.27 | 10:17 | 4.59 | trailing_stop | $+130.00 |
| 35 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00157500 | 10:10 | 3.65 | 10:27 | 4.70 | trailing_stop | $+103.00 |
| 36 | 2026-11-19 | AAPL | short | squeeze | AAPL261120P00347500 | 10:26 | 2.27 | 10:40 | 2.44 | trailing_stop | $+15.00 |
| 37 | 2026-11-19 | SPY | short | pullback | SPY261119P00728000 | 10:47 | 3.69 | 10:57 | 3.20 | trailing_stop | $-51.00 |
| 38 | 2026-11-19 | NVDA | short | pullback | NVDA261120P00152500 | 10:47 | 3.00 | 10:55 | 2.70 | trailing_stop | $-32.00 |
| 39 | 2026-11-19 | SPY | short | pullback | SPY261119P00729000 | 11:17 | 3.36 | 11:28 | 2.68 | trailing_stop | $-70.00 |
| 40 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00663000 | 11:30 | 3.73 | 11:31 | 3.28 | trailing_stop | $-47.00 |
| 41 | 2026-11-19 | SPY | long | squeeze | SPY261119C00731000 | 11:37 | 2.60 | 11:43 | 2.40 | trailing_stop | $-22.00 |
| 42 | 2026-11-19 | QQQ | long | squeeze | QQQ261119C00664000 | 11:37 | 3.77 | 11:43 | 3.50 | trailing_stop | $-29.00 |
| 43 | 2026-11-19 | NVDA | long | squeeze | NVDA261120C00155000 | 11:37 | 1.89 | 11:43 | 1.78 | trailing_stop | $-13.00 |
| 44 | 2026-11-19 | AAPL | long | squeeze | AAPL261120C00352500 | 11:37 | 1.49 | 11:43 | 1.55 | trailing_stop | $+4.00 |
| 45 | 2026-11-19 | TSLA | long | squeeze | TSLA261120C00385000 | 11:37 | 4.31 | 11:43 | 4.23 | trailing_stop | $-10.00 |
| 46 | 2026-11-19 | TSLA | short | pullback | TSLA261120P00382500 | 11:50 | 5.60 | 11:53 | 8.64 | trailing_stop | $+302.00 |
| 47 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 10:41 | 2.32 | 10:49 | 2.29 | trailing_stop | $-5.00 |
| 48 | 2026-11-20 | QQQ | short | pullback | QQQ261120P00628000 | 10:58 | 4.62 | 11:06 | 4.86 | trailing_stop | $+22.00 |
| 49 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00365000 | 10:58 | 4.77 | 11:09 | 4.53 | trailing_stop | $-26.00 |
| 50 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:04 | 2.17 | 11:06 | 1.84 | trailing_stop | $-35.00 |
| 51 | 2026-11-20 | TSLA | short | pullback | TSLA261120P00362500 | 11:17 | 3.55 | 11:50 | 7.33 | trailing_stop | $+376.00 |
| 52 | 2026-11-20 | AAPL | short | pullback | AAPL261120P00350000 | 11:20 | 2.92 | 11:55 | 4.20 | trailing_stop | $+126.00 |
| 53 | 2026-11-20 | NVDA | short | pullback | NVDA261120P00137000 | 11:26 | 1.65 | 11:50 | 1.92 | trailing_stop | $+25.00 |
| 54 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00651000 | 10:12 | 4.44 | 10:43 | 6.26 | trailing_stop | $+180.00 |
| 55 | 2026-11-23 | SPY | long | pullback | SPY261123C00722000 | 10:13 | 3.87 | 10:42 | 5.70 | trailing_stop | $+181.00 |
| 56 | 2026-11-23 | AAPL | long | squeeze | AAPL261123C00350000 | 10:18 | 1.44 | 10:45 | 2.61 | trailing_stop | $+115.00 |
| 57 | 2026-11-23 | TSLA | short | squeeze | TSLA261123P00370000 | 10:46 | 0.20 | 10:56 | 0.24 | trailing_stop | $+2.00 |
| 58 | 2026-11-23 | QQQ | short | pullback | QQQ261123P00651000 | 11:03 | 4.02 | 11:05 | 3.28 | trailing_stop | $-76.00 |
| 59 | 2026-11-23 | SPY | long | squeeze | SPY261123C00726000 | 11:13 | 2.43 | 11:15 | 1.93 | trailing_stop | $-52.00 |
| 60 | 2026-11-23 | QQQ | long | pullback | QQQ261123C00653000 | 11:13 | 3.63 | 11:15 | 2.80 | trailing_stop | $-85.00 |
| 61 | 2026-11-23 | AAPL | short | pullback | AAPL261123P00350000 | 11:27 | 2.22 | 11:33 | 2.13 | trailing_stop | $-11.00 |
| 62 | 2026-11-23 | SPY | short | squeeze | SPY261123P00723000 | 11:36 | 2.69 | 11:43 | 4.62 | trailing_stop | $+191.00 |
| 63 | 2026-11-23 | QQQ | short | squeeze | QQQ261123P00651000 | 11:36 | 3.10 | 11:43 | 5.21 | trailing_stop | $+209.00 |
| 64 | 2026-11-23 | AAPL | short | squeeze | AAPL261123P00347500 | 11:39 | 1.10 | 11:43 | 1.16 | trailing_stop | $+4.00 |
| 65 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00636000 | 10:39 | 3.65 | 10:45 | 4.68 | trailing_stop | $+101.00 |
| 66 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00155000 | 10:43 | 4.83 | 10:45 | 5.45 | trailing_stop | $+60.00 |
| 67 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00380000 | 10:59 | 6.30 | 11:20 | 7.06 | trailing_stop | $+74.00 |
| 68 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00634000 | 11:00 | 3.60 | 11:09 | 3.68 | trailing_stop | $+6.00 |
| 69 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:00 | 4.13 | 11:08 | 4.18 | trailing_stop | $+3.00 |
| 70 | 2026-11-24 | SPY | short | pullback | SPY261124P00715000 | 11:01 | 3.41 | 11:09 | 3.35 | trailing_stop | $-8.00 |
| 71 | 2026-11-24 | AAPL | short | squeeze | AAPL261125P00350000 | 11:02 | 2.57 | 11:07 | 2.48 | trailing_stop | $-11.00 |
| 72 | 2026-11-24 | TSLA | short | pullback | TSLA261125P00377500 | 11:29 | 6.13 | 11:43 | 6.10 | trailing_stop | $-5.00 |
| 73 | 2026-11-24 | NVDA | short | pullback | NVDA261125P00152500 | 11:30 | 4.50 | 11:34 | 4.25 | trailing_stop | $-27.00 |
| 74 | 2026-11-24 | SPY | short | pullback | SPY261124P00714000 | 11:37 | 2.66 | 11:44 | 2.42 | trailing_stop | $-26.00 |
| 75 | 2026-11-24 | QQQ | short | pullback | QQQ261124P00633000 | 11:37 | 3.35 | 11:43 | 2.98 | trailing_stop | $-39.00 |
| 76 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 10:17 | 3.88 | 10:31 | 3.65 | trailing_stop | $-25.00 |
| 77 | 2026-11-25 | TSLA | short | squeeze | TSLA261125P00360000 | 10:21 | 2.73 | 10:33 | 1.88 | trailing_stop | $-87.00 |
| 78 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00144000 | 10:27 | 2.38 | 10:33 | 2.00 | trailing_stop | $-40.00 |
| 79 | 2026-11-25 | QQQ | long | pullback | QQQ261125C00613000 | 10:36 | 4.51 | 10:39 | 3.89 | trailing_stop | $-64.00 |
| 80 | 2026-11-25 | TSLA | long | pullback | TSLA261125C00365000 | 10:56 | 3.02 | 10:57 | 2.41 | trailing_stop | $-63.00 |
| 81 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00143000 | 10:58 | 2.05 | 11:14 | 2.06 | trailing_stop | $-1.00 |
| 82 | 2026-11-25 | SPY | short | pullback | SPY261125P00700000 | 11:00 | 3.70 | 11:14 | 3.42 | trailing_stop | $-30.00 |
| 83 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00611000 | 11:00 | 3.92 | 11:21 | 3.50 | trailing_stop | $-44.00 |
| 84 | 2026-11-25 | AAPL | short | pullback | AAPL261125P00347500 | 11:02 | 2.47 | 11:11 | 2.66 | trailing_stop | $+17.00 |
| 85 | 2026-11-25 | NVDA | short | pullback | NVDA261125P00142000 | 11:32 | 1.65 | 11:51 | 1.45 | trailing_stop | $-22.00 |
| 86 | 2026-11-25 | SPY | short | pullback | SPY261125P00699000 | 11:44 | 3.06 | 11:45 | 2.81 | trailing_stop | $-27.00 |
| 87 | 2026-11-25 | QQQ | short | pullback | QQQ261125P00610000 | 11:44 | 3.27 | 11:45 | 2.99 | trailing_stop | $-30.00 |
