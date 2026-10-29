QUANTCONNECT FEASIBLE: the free cloud data has SPY same-day expirations (weekly Fridays from 2012, Mon/Wed/Fri from 2018, every day from 2023), SPXW listings, minute quotes for every checked same-day contract, and working fills at the bid/ask; the 10 KB-per-backtest log cap is the main constraint.

T16: QuantConnect data feasibility for SPY/SPX same-day options (data check only; no strategy results)

Run 2026-10-29 with QuantConnect cloud backtests on the free plan. Nothing was downloaded locally. QuantConnect's data terms restrict redistribution, so this report shows only counts and summary statistics, with no raw quotes.

## Same-day expirations per year

| Year | Trading days | SPY same-day expirations | SPXW same-day expirations | Days with no SPY chain | Days with no SPXW chain |
|---|---|---|---|---|---|
| 2012 | 250 | 41 | 37 | 0 | 24 |
| 2013 | 252 | 42 | 38 | 0 | 0 |
| 2014 | 252 | 44 | 42 | 0 | 0 |
| 2015 | 252 | 54 | 47 | 0 | 0 |
| 2016 | 252 | 71 | 107 | 0 | 0 |
| 2017 | 251 | 104 | 157 | 0 | 0 |
| 2018 | 251 | 148 | 158 | 0 | 0 |
| 2019 | 252 | 157 | 161 | 0 | 0 |
| 2020 | 253 | 159 | 160 | 0 | 0 |
| 2021 | 252 | 157 | 159 | 0 | 0 |
| 2022 | 251 | 170 | 220 | 0 | 0 |
| 2023 | 250 | 250 | 250 | 0 | 0 |
| 2024 | 252 | 252 | 252 | 0 | 0 |
| 2025 | 250 | 250 | 250 | 0 | 0 |
| Total | 3520 | 1899 | 2038 | 0 | 24 |

## Same-day expirations per weekday (share of that weekday's trading days)

| Year | SPY Mon | SPY Tue | SPY Wed | SPY Thu | SPY Fri | SPXW Mon | SPXW Tue | SPXW Wed | SPXW Thu | SPXW Fri |
|---|---|---|---|---|---|---|---|---|---|---|
| 2012 | 1/47 | 0/50 | 0/51 | 1/51 | 39/51 | 0/47 | 0/50 | 0/51 | 1/51 | 36/51 |
| 2013 | 1/48 | 1/52 | 0/51 | 1/50 | 39/51 | 0/48 | 0/52 | 0/51 | 0/50 | 38/51 |
| 2014 | 2/48 | 1/52 | 1/52 | 1/50 | 39/50 | 0/48 | 1/52 | 1/52 | 1/50 | 39/50 |
| 2015 | 0/48 | 2/52 | 1/52 | 4/51 | 47/49 | 2/48 | 2/52 | 1/52 | 5/51 | 37/49 |
| 2016 | 0/46 | 0/52 | 17/52 | 3/51 | 51/51 | 18/46 | 3/52 | 44/52 | 3/51 | 39/51 |
| 2017 | 0/46 | 0/51 | 52/52 | 1/51 | 51/51 | 46/46 | 9/51 | 52/52 | 3/51 | 47/51 |
| 2018 | 43/48 | 3/51 | 50/50 | 1/51 | 51/51 | 48/48 | 7/51 | 50/50 | 2/51 | 51/51 |
| 2019 | 48/48 | 6/52 | 51/51 | 1/50 | 51/51 | 48/48 | 7/52 | 51/51 | 4/50 | 51/51 |
| 2020 | 48/48 | 6/52 | 52/52 | 4/52 | 49/49 | 48/48 | 6/52 | 52/52 | 5/52 | 49/49 |
| 2021 | 47/47 | 5/52 | 52/52 | 3/51 | 50/50 | 47/47 | 7/52 | 52/52 | 3/51 | 50/50 |
| 2022 | 45/45 | 13/52 | 52/52 | 9/51 | 51/51 | 45/45 | 38/52 | 52/52 | 34/51 | 51/51 |
| 2023 | 45/45 | 51/51 | 52/52 | 51/51 | 51/51 | 45/45 | 51/51 | 52/52 | 51/51 | 51/51 |
| 2024 | 48/48 | 53/53 | 50/50 | 50/50 | 51/51 | 48/48 | 53/53 | 50/50 | 50/50 | 51/51 |
| 2025 | 48/48 | 52/52 | 52/52 | 48/48 | 50/50 | 48/48 | 52/52 | 52/52 | 48/48 | 50/50 |

## Quote quality

Ordinary days (12, drawn with seed 16 from SPY same-day-expiration days spread across 2016-2023): 2016-11-04, 2017-11-08, 2018-10-08, 2019-03-01, 2020-01-10, 2020-03-31, 2021-03-01, 2021-09-10, 2022-02-11, 2023-01-17, 2023-05-18, 2023-08-10. Stress days: 2018-02-05, 2018-02-06, 2020-03-09, 2020-03-12, 2020-03-16, 2022-09-13, 2024-08-05.
For each day at 9:45, 12:00 and 15:00: the out-of-the-money put and call nearest to 0.5%, 1% and 2% from SPY's price, using the last 1-minute quote bar before that time (bid and ask at the bar's close). Where SPY had no same-day expiration, the nearest expiration is used and shown separately.

| Group | Day type | Distance | Quotes checked | Two-sided | Zero or missing bid | No quote bar in the last minute | Median spread ($) | Median spread (% of mid) | 90th pct spread (% of mid) |
|---|---|---|---|---|---|---|---|---|---|
| ordinary | same-day | 0.5% | 72 | 97% | 2 | 0 | 0.01 | 7.3% | 40.0% |
| ordinary | same-day | 1.0% | 72 | 92% | 6 | 0 | 0.01 | 11.4% | 66.7% |
| ordinary | same-day | 2.0% | 72 | 60% | 29 | 0 | 0.01 | 9.5% | 66.7% |
| stress | same-day | 0.5% | 14 | 100% | 0 | 0 | 0.09 | 4.1% | 6.7% |
| stress | same-day | 1.0% | 14 | 100% | 0 | 0 | 0.09 | 5.0% | 7.6% |
| stress | same-day | 2.0% | 14 | 100% | 0 | 0 | 0.04 | 7.4% | 15.3% |
| stress | nearest expiry | 0.5% | 22 | 100% | 0 | 0 | 0.04 | 1.6% | 8.2% |
| stress | nearest expiry | 1.0% | 22 | 100% | 0 | 0 | 0.05 | 2.4% | 9.4% |
| stress | nearest expiry | 2.0% | 22 | 100% | 0 | 0 | 0.06 | 3.4% | 25.4% |

| Day | Type | Expiry used | 9:45 two-sided | 12:00 two-sided | 15:00 two-sided | Median spread (% of mid) |
|---|---|---|---|---|---|---|
| 2016-11-04 | ordinary | same day | 5/6 | 5/6 | 5/6 | 22.2% |
| 2017-11-08 | ordinary | same day | 3/6 | 2/6 | 2/6 | 40.0% |
| 2018-02-05 | stress | next (2018-02-07) | 6/6 | 6/6 | 6/6 | 3.2% |
| 2018-02-06 | stress | next (2018-02-07) | 6/6 | 6/6 | 6/6 | 9.5% |
| 2018-10-08 | ordinary | same day | 4/6 | 5/6 | 5/6 | 11.4% |
| 2019-03-01 | ordinary | same day | 5/6 | 5/6 | 4/6 | 13.0% |
| 2020-01-10 | ordinary | same day | 3/6 | 3/6 | 4/6 | 23.4% |
| 2020-03-09 | stress | same day | 0/0 | 6/6 | 6/6 | 4.4% |
| 2020-03-12 | stress | next (2020-03-13) | 0/0 | 6/6 | 6/6 | 2.3% |
| 2020-03-16 | stress | same day | 0/0 | 6/6 | 6/6 | 5.6% |
| 2020-03-31 | ordinary | same day | 6/6 | 6/6 | 6/6 | 5.2% |
| 2021-03-01 | ordinary | same day | 6/6 | 5/6 | 5/6 | 9.5% |
| 2021-09-10 | ordinary | same day | 5/6 | 6/6 | 6/6 | 15.4% |
| 2022-02-11 | ordinary | same day | 6/6 | 6/6 | 6/6 | 3.9% |
| 2022-09-13 | stress | next (2022-09-14) | 6/6 | 6/6 | 6/6 | 1.2% |
| 2023-01-17 | ordinary | same day | 6/6 | 6/6 | 6/6 | 6.9% |
| 2023-05-18 | ordinary | same day | 5/6 | 5/6 | 5/6 | 13.3% |
| 2023-08-10 | ordinary | same day | 5/6 | 6/6 | 6/6 | 8.0% |
| 2024-08-05 | stress | same day | 6/6 | 6/6 | 6/6 | 4.4% |

Snapshots with no SPY price or no option chain: 2020-03-09 9:45, 2020-03-12 9:45, 2020-03-16 9:45.

## Iron condor plumbing (mechanics check, not a result)

On 3 ordinary days: short put and call nearest 1% out of the money, long legs $2 further out, one contract each, opened with market orders at 9:45 and closed at 15:00. The table only checks that each order filled and at which side of the quote; no profit or loss is reported.

| Day | Leg | Open: filled | Open fill at | Close: filled | Close fill at |
|---|---|---|---|---|---|
| 2016-11-04 | short put | yes | bid | yes | ask |
| 2016-11-04 | long put | yes | ask | yes | bid |
| 2016-11-04 | short call | yes | bid | yes | ask |
| 2016-11-04 | long call | yes | ask | yes | ask (bid was $0; LEAN filled the sale at the ask) |
| 2020-03-31 | short put | yes | bid | yes | ask |
| 2020-03-31 | long put | yes | ask | yes | bid |
| 2020-03-31 | short call | yes | bid | yes | ask |
| 2020-03-31 | long call | yes | ask | yes | bid |
| 2023-08-10 | short put | yes | bid | yes | ask |
| 2023-08-10 | long put | yes | ask | yes | bid |
| 2023-08-10 | short call | yes | bid | yes | bid = ask (locked quote) |
| 2023-08-10 | long call | yes | ask | yes | bid = ask (locked quote) |

## Notes

- **Missing Fridays in 2012-2016 have a known cause.** Until February 2015 the monthly SPY options carried a Saturday expiration date (trading still ended on the Friday), so 12 third Fridays a year show no same-day SPY expiration. SPXW weeklies skipped the third Friday (the monthly SPX options were AM-settled standard SPX) until about 2016-2017. The few Mon/Tue/Thu expirations before daily listings are holiday-shifted or quarter-end contracts.
- **No 9:45 snapshot on 2020-03-09, 03-12 and 03-16.** Market-wide circuit breakers halted trading shortly after the open on those days, so there was no SPY minute bar in the 5 minutes before 9:45. The 12:00 and 15:00 snapshots are complete.
- **Several stress days had no same-day SPY expiration** (Tuesdays and a Thursday before SPY had daily expirations, which began in late 2022). Those rows use the next expiration and are shown separately.
- **Zero bids are a market feature, not missing data.** The 29 zero bids among the 72 same-day 2%-away quotes on ordinary days are far out-of-the-money options worth less than a cent or two; every checked contract had a quote bar in the minute before the check.
- **Spreads in % of mid are large because these options are cheap.** The median spread is $0.01 on ordinary days, which is 7-11% of the mid price.
- **LEAN fill-model quirk.** On 2016-11-04 a long call with a $0 bid was sold at the $0.01 ask by LEAN's default fill model. A real test should use a fill model that fills sales at the bid, including a $0 bid.
- **SPXW was checked for listings only.** The quote checks are SPY only, as the task asked. QuantConnect has no SPXW chain on 24 trading days in 2012.
- **Holdout.** 2024-2025 appear only in this data check (expiration counts and 2024-08-05 quotes), as the instruction asked; no strategy was run on them.

## Free-plan limits met

| Limit | What we met |
|---|---|
| Plan | Free organization: 1 seat, 1 backtest node (B-MICRO), 1 research node (not used). |
| Concurrency | One cloud backtest at a time (one node), so the 6 runs were made one after another. |
| Backtest time | The 2012-2025 expiry scan (daily SPY, two option-chain listings a day) took 14 minutes; each quote run took about 22 seconds; compiles 1-3 seconds. No time limit was hit. QuantConnect's docs say the free node adds a 20-second launch delay and allows 200 backtests a day. |
| Logs | 10 KB of log per backtest on the free plan (3 MB of log reading a day). This was the binding limit: output had to be packed to one line per snapshot and the 19 quote days split into 4 backtests (largest log 6.8 KB). |
| Data | SPY equity options, SPX/SPXW index options and SPY minute bars were all usable in cloud backtests at no charge; the account's credit balance was unchanged after all runs. Tick and second data are not in the free plan (not needed here). Downloading this data for local use would be a paid purchase; it was not attempted. |

## Verdict

QUANTCONNECT FEASIBLE: the free cloud data has SPY same-day expirations (weekly Fridays from 2012, Mon/Wed/Fri from 2018, every day from 2023), SPXW listings, minute quotes for every checked same-day contract, and working fills at the bid/ask; the 10 KB-per-backtest log cap is the main constraint.
