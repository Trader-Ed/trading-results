BENCH AUDIT: PROBLEM FOUND

# T17: bench audit, can the bench say yes? (2019-2023, all9; holdout untouched; rules unchanged)

Run 2026-10-29.

## Findings

- **The problem: the bench almost never says yes, even to a real edge.** None of the 180 planted sets passed, at any size or edge, including a 55% edge with 26,750 signals. The calculations are right (see the next three points), but the pass bar is too demanding for edges of this size.
- **First reason: the 10-minute requirement.** A direction edge at +30 minutes shows up only partly at +10 minutes (about 51.5% vs 54.5% here), so the 10-minute z is about a third of the 30-minute z. At the median row size a 55% edge reaches z +5.0 at 30 minutes in all9, but only +1.8 at 10 minutes.
- **Second reason: spy has to pass on its own, with a ninth of the signals.** At the median size spy has about 630 signals, so even its 30-minute z averages only +1.9 for a 55% edge. With 26,750 signals in all9, all9 met the bar in 19 of 20 repeats at 55% and 9 of 20 at 53%, but spy met it in none (30-minute z +3.8, 10-minute z +1.2).
- **No false passes.** Pure noise passed 0 of 60 sets and met the bar in either universe 0 times. The z values follow the planted edge as theory predicts: at the median size +5.0, +3.7 and +1.5 at 30 minutes for 55%, 53% and 51%, against a rough expectation of +5.3, +3.2 and +1.1 (all values in the table).
- **The trade evaluation is exact.** Adding +0.10R and +0.20R to every T13 trade raises average R after costs, gross R and the strict-rule R by +0.1000 and +0.2000 (to 4 decimals); recomputing with no edge reproduces T13's stored R exactly.
- **What it means for earlier results:** a "FAIL" from T10/T10b says "not shown", not "no edge". An edge of 53-55% at 30 minutes, which would matter for trading, would usually have been failed by the bar as written. Changing the bar (for example judging the 30-minute horizon alone, or pooling all9 without a separate spy test) is a partner decision; nothing was changed here.

## Detection table (20 repeats each; a set passes when it meets the normal pass bar in BOTH all9 and spy)

| Size (all9 / spy signals) | Planted edge at +30 min | Passed | Met the bar in all9 | Met the bar in spy | Share our way at 30 min (all9) | at 10 min | z at 30 / 10 min (all9) | z at 30 / 10 min (spy) | Expected z 30 / 10 (all9) |
|---|---|---|---|---|---|---|---|---|---|
| median: 5,642 / ~627 | 55% | 0/20 | 0/20 | 1/20 | 54.4% | 51.1% | +5.0 / +1.8 | +1.9 / +0.9 | +5.3 / +2.1 |
| median: 5,642 / ~628 | 53% | 0/20 | 1/20 | 0/20 | 52.7% | 50.4% | +3.7 / +1.6 | +1.1 / +0.5 | +3.2 / +1.2 |
| median: 5,642 / ~635 | 51% | 0/20 | 0/20 | 0/20 | 50.7% | 49.7% | +1.5 / +0.7 | +0.5 / +0.4 | +1.1 / +0.4 |
| median: 5,642 / ~613 | none (random) | 0/20 | 0/20 | 0/20 | 49.7% | 49.2% | +0.2 / +0.2 | +0.1 / +0.2 | +0.0 / +0.0 |
| p25: 1,890 / ~211 | 55% | 0/20 | 0/20 | 0/20 | 54.5% | 51.3% | +3.1 / +1.4 | +1.1 / +0.3 | +3.1 / +1.2 |
| p25: 1,890 / ~212 | 53% | 0/20 | 0/20 | 0/20 | 52.3% | 50.3% | +1.5 / +0.8 | +0.2 / -0.1 | +1.8 / +0.7 |
| p25: 1,890 / ~215 | 51% | 0/20 | 0/20 | 0/20 | 50.9% | 49.5% | +0.6 / -0.1 | +0.5 / +0.2 | +0.6 / +0.2 |
| p25: 1,890 / ~212 | none (random) | 0/20 | 0/20 | 0/20 | 49.6% | 49.2% | +0.1 / +0.0 | +0.1 / +0.3 | +0.0 / +0.0 |
| p75: 26,750 / ~2,966 | 55% | 0/20 | 19/20 | 0/20 | 54.5% | 51.3% | +11.8 / +4.5 | +3.8 / +1.2 | +11.6 / +4.5 |
| p75: 26,750 / ~2,961 | 53% | 0/20 | 9/20 | 0/20 | 52.5% | 50.5% | +6.8 / +2.8 | +2.3 / +0.7 | +6.9 / +2.7 |
| p75: 26,750 / ~2,958 | 51% | 0/20 | 1/20 | 0/20 | 50.5% | 49.6% | +2.4 / +0.9 | +0.8 / +0.6 | +2.3 / +0.9 |
| p75: 26,750 / ~2,981 | none (random) | 0/20 | 0/20 | 0/20 | 49.5% | 49.3% | -0.1 / +0.2 | +0.0 / +0.2 | +0.0 / +0.0 |

## Planted trade edge (T13 Part A trades, 2016-2023, normal R-after-costs evaluation)

| Added before costs | Trades | Avg R after costs: before -> after (change) | Gross R change | Strict rule change | z: before -> after | z vs opposite: before -> after |
|---|---|---|---|---|---|---|
| +0.10R | 32,232 | -0.1600 -> -0.0600 (+0.1000) | +0.1000 | +0.1000 | -5.5 -> -2.1 | +8.6 -> +11.3 |
| +0.20R | 32,232 | -0.1600 -> +0.0400 (+0.2000) | +0.2000 | +0.2000 | -5.5 -> +1.4 | +8.6 -> +14.1 |

Recomputing every trade's R with no edge reproduces T13's stored values to within 0.0e+00R. T13's cost of 0.05% of price per side also applies to the extra exit distance: longs pay a little more and shorts a little less, which nets out to under 0.0001R.

## Checks behind the verdict

- Pure noise passes at most 1 of 20 at every size, and meets the bar in either universe at most 2 of 20: yes (passed 0 of 60 in all).
- Detection rises with the planted edge at every size: yes.
- A 55% edge is found in at least 18 of 20 repeats at the large size: no.
- The planted trade edge comes back at the amount added (within 0.001R after costs, exactly before costs): yes.

## Method

Planted direction edges: signals at random moments on all9 (a random symbol, a random research day that is
not an FOMC day, a random whole decision minute in the T10 entry window 9:35-11:50). The direction is set
from the ACTUAL move to +30 minutes, for this audit only: with probability p it is the direction the stock
then moved (p = 55%, 53%, 51%), otherwise the opposite; a zero move gets a random direction. Pure noise:
the same with a random direction. Each set then goes through the normal T10b signal test unchanged:
signals.add_moves (moves and the other-day control) and stats.row_stats (the pass bar), in all9 and in spy;
a set passes when both meet the bar, as for any rule. 20 repeats per setting, at three sizes: the median
T10b row (5,642 signals in all9) and its 25th and 75th percentiles (1,890 and 26,750).
Planted trade edge: T13 Part A's trades (2016-2023) with +0.10R or +0.20R added to every trade before costs
(the exit moved that far our way, costs recomputed with T13's own formula), then t13.a_summary.
Expected z: a rough guide only, (edge in share) / (0.71 / sqrt(n)) with the 10-minute share edge derived from a random walk (the sign at 10 minutes agrees with the sign at 30 minutes about 70% of the time); day clustering and the control's own noise make real z values somewhat lower.
