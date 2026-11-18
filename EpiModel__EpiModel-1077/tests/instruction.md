# Issue

**Title:** Let the edges correction count only tie-eligible nodes

## Description

`edges_correct()` rescales the edges coefficient every time step by `log(N_old) - log(N_new)`, so that mean degree is preserved as the population changes. It counts `N` as `sum(active == 1)`, every active node. That is right whenever every active node can form a tie, which is the usual case.

It is wrong when a model carries a subpopulation that stays active but is structurally excluded from the network. ARTnet's sexual-cessation configuration is the case I hit: every target statistic for the retired age band is zero, `ergm` pins those terms at `-Inf`, and no tie incident to a retired node can ever form. The population the correction sees grows while the population that can hold an edge does not, so the whole of the adjustment lands on the nodes that can.

## What it costs

Measured in an HIV model with cessation at 65, at 25,000 nodes over 25 years, matching the arithmetic to four decimals:

| quantity | start | end |
|---|---|---|
| `sum(active == 1)` | 25,000 | 30,512 |
| nodes able to form ties | 24,789 | 24,789 |
| edges coefficient drift | | -0.1992, exactly `log(25000 / 30512)` |
| mean degree among those nodes | | **-18.1%** |

The same model without a cessation band drifts +0.0071 over the same run. A controlled comparison at 100,000 nodes over fifty years lost all three bacterial sexually transmitted infections and put HIV incidence 35% lower.

It is easy to miss for three reasons. It does not appear in `netdx()`, which runs on the fitted network before any node has been excluded. The rest of the model looks healthy, so it reads as an ordinary calibration offset. And calibrating around it hides it, by absorbing the thinning into compensating transmission probabilities that are then wrong wherever the excluded share differs.

## The change

A new `edges.correct.attr` control names a binary nodal attribute marking the nodes eligible to form ties. `update_sim_num()` maintains their counts alongside the existing ones, so the previous-value contract is unchanged. Default is `NULL`, which counts every active node exactly as before.

`edges_correct()` also now leaves the coefficients alone, with a warning naming the time step, when the adjustment is not finite. An empty count made it infinite, and an infinite or `NaN` value added to an edges coefficient causes every proposed tie to be rejected for the rest of the run. That presents as a slow collapse of the network rather than as an error, which is a bad failure mode to leave in place.

## Backwards compatibility

The default path is unchanged, checked three ways:

- The test file carries a verbatim copy of the pre-change function and asserts the new one produces an identical `nwparam` across a grid of growing and shrinking populations, for one group and for two, so the test cannot drift away from the old behavior.
- An end-to-end `netsim()` with vital dynamics at a fixed seed, where the population grows from 200 to 369, returns `identical()` output on this branch and on `main`, under both `tergmLite = TRUE` and `tergmLite = FALSE`. Both were built clean from source into separate libraries for the comparison.
- 189 existing tests across the network test files pass unchanged.

50 new assertions cover the default path, the eligible path for one and two groups, `NA` treated as ineligible, a restart carrying no stored eligible count, the non-finite guard, attribute mis-specification, the counts `update_sim_num()` maintains, and a 300-step property check that cumulative drift is zero with the control set and `log(1 / 1.25)` without it.

One aside worth recording: population counts are integers, and a product of two of them overflows 32-bit arithmetic above roughly 46,000 per factor. R returns `NA` with a warning rather than promoting to double, and an `NA` reaching the edges coefficient collapses the network silently. The two-group harmonic mean here is safe because the leading `2` is a double literal, but the new tests check the adjustment is finite at realistic population sizes so it stays that way.

Reported downstream as EpiModel/EpiModelHIV-p#399.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `706d0e199a6e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.