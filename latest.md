T17b OUTCOME: CANDIDATES FOUND

# T17b: the corrected pass bar for direction signal tests (partner decision, October 29)

Run 2026-10-29. Nothing new was downloaded or tested: the T17 audit was re-run with the new bar, and the saved T10b and T11 signals (2019-2023) and T13 Part B's 2016-2018 re-runs were re-judged. Holdout untouched; rulebook.yaml unchanged.

**New bar.** The 30-minute horizon decides (10 and 60 minutes reported, not required). The share moving our way beats the matched control by z >= 3, clustered by day, in all9, and spy's share gap has the same sign (no separate 3-SE test). At least 300 signals. The 30-minute share gap is positive in at least 4 of the 5 years.

## Findings

- **The new bar can say yes, and it doesn't say yes to noise.** At the median signal-test size it finds a planted 55% edge in 19 of 20 repeats and a 53% edge in 12 of 20 (the old bar: 0 and 0). At the large size it finds 55% and 53% every time. Pure noise passed 0 of 60 sets.
- **One candidate in the saved results: T11's Keltner momentum long on 5-minute bars (kc_mom_p6_m2: a close above the 6-bar Keltner band at 2 ATR).** In 2019-2023 the price was up 30 minutes later 55.2% of the time against 49.9% for the matched control (z +3.4), positive in all 5 years, and spy points the same way. Its average 30-minute move was +0.077%, or +0.064% more than the control.
- **It held on 2016-2018,** the confirmation years it was never fitted on: 53.9% vs 48.5% (z +3.1), positive in all 3 years. But the average move there was only +0.028%.
- **The move per trade is about the size of the spread.** After a rough cost of one quoted spread (0.034% of price, the median for the nine stocks in T14's tick data): about +0.04% per trade on 2019-2023 and about -0.01% on 2016-2018. It is a real direction effect, but too small to trade in shares as it stands. The next step would be a proper cost test of this one rule, which is a partner decision.
- **Expected chance passes: about 0.24** across the 180 candidates, so one pass that also holds on independent years is unlikely to be luck. The same rule on 15-minute bars is the closest near miss (z +2.3, 5 of 5 years).

## Audit with the new bar (20 repeats each; T10 bar shown for comparison)

| Size (all9 / spy signals) | Planted edge at +30 min | Passed, new bar | Passed, T10 bar | z at 30 min (all9) |
|---|---|---|---|---|
| median: 5,642 / ~627 | 55% | 19/20 | 0/20 | +5.0 |
| median: 5,642 / ~628 | 53% | 12/20 | 0/20 | +3.7 |
| median: 5,642 / ~635 | 51% | 2/20 | 0/20 | +1.5 |
| median: 5,642 / ~613 | none (pure noise) | 0/20 | 0/20 | +0.2 |
| p25: 1,890 / ~211 | 55% | 8/20 | 0/20 | +3.1 |
| p25: 1,890 / ~212 | 53% | 2/20 | 0/20 | +1.5 |
| p25: 1,890 / ~215 | 51% | 0/20 | 0/20 | +0.6 |
| p25: 1,890 / ~212 | none (pure noise) | 0/20 | 0/20 | +0.1 |
| p75: 26,750 / ~2,966 | 55% | 20/20 | 0/20 | +11.8 |
| p75: 26,750 / ~2,961 | 53% | 20/20 | 0/20 | +6.8 |
| p75: 26,750 / ~2,958 | 51% | 7/20 | 0/20 | +2.4 |
| p75: 26,750 / ~2,981 | none (pure noise) | 0/20 | 0/20 | -0.1 |

False passes on pure noise: 0 of 60 sets (the limit set for going on was about 1 in 20).

## Re-judged saved results

Comparisons: 180 rule x side x bar-size candidates (98 from T10b, 82 from T11), one 3-SE test each (all9, 30 minutes). If no rule had an edge, about 0.24 would pass by chance at most (spy's same-sign check and the years check only lower it).

| Set | Rule | Signals (all9 / spy) | Share our way at 30 min vs control | z at 30 min | spy share gap | Years positive | z at 10 / 60 min | Avg move at 30 min (vs control) | 2016-2018 (all9): share vs control, z, avg move, years + | Rough after-cost move per trade |
|---|---|---|---|---|---|---|---|---|---|---|
| T11 | kc_mom_p6_m2 long, 5m bars | 4,348 / 455 | 55.2% vs 49.9% | +3.4 | +4.0 pts | 5/5 | +2.1 / +2.8 | +0.077% (+0.064%) | 53.9% vs 48.5%, z +3.1, +0.028% (vs control +0.052%), 3/3 | 2019-2023: +0.043%; 2016-2018: -0.006% |

After-cost estimate: the average 30-minute move our way minus one full quoted spread for the round trip (buy at the ask, sell at the bid), 0.034% of price: the median spread of the nine stocks in T14's tick sample (13 quotes, taken at 9:35-9:40 breakout moments, when spreads are wider than later in the morning). Sale fees are under 0.003% and left out. This is a rough per-trade figure, not a backtest: no position limits, no overlapping signals removed, and the average move includes the market's drift (the move versus the control is shown beside it).

## Closest other candidates (by z at 30 minutes; none passes)

| Set | Rule | Signals (all9) | z at 30 min | Share gap (pts) | Years + | spy gap (pts) | Avg move at 30 min |
|---|---|---|---|---|---|---|---|
| T10b | gap0.5_cont short | 2,764 | +2.5 | +4.9 | 5/5 | +10.7 | +0.047% |
| T11 | kc_mom_p6_m2 long, 15m bars | 4,150 | +2.3 | +3.8 | 5/5 | +1.6 | +0.054% |
| T10b | gap1_cont long | 1,638 | +1.9 | +4.6 | 5/5 | +12.9 | +0.072% |
| T10b | gap1_cont short | 1,565 | +1.9 | +4.8 | 4/5 | +25.3 | +0.036% |
| T11 | kc_mom_p20_m2 long, 15m bars | 22,420 | +1.9 | +1.6 | 4/5 | +2.0 | +0.024% |
| T10b | b3_reentry long, 5m bars | 9,646 | +1.8 | +1.8 | 4/5 | +1.6 | +0.008% |
| T11 | kc_mom_p6_m1.3 long, 5m bars | 14,607 | +1.8 | +1.6 | 4/5 | +0.3 | +0.028% |
| T11 | kc_mom_p6_m2 short, 5m bars | 3,732 | +1.6 | +2.8 | 4/5 | +2.1 | -0.004% |

---

Full per-trade tables: [history/2026-10-29-t17b-corrected-pass-bar.md](history/2026-10-29-t17b-corrected-pass-bar.md)
