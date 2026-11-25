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

---

Full per-trade tables: [history/2026-11-25-v2-variant-replay-dls-lock.md](history/2026-11-25-v2-variant-replay-dls-lock.md)
