# Issue

**Title:** Add cumulative degree distribution plot to plot.netdx

## Description

.

Adds `plot.netdx(type = "cumldeg")` for the cumulative degree distribution, plus `get_degree_dist()`, an exported helper that returns the cumulative or momentary distribution as a data frame. Both work off the timed edgelist, so they need `netdx(keep.tedgelist = TRUE)`.

`momentary = TRUE` overlays the momentary degree distribution computed over the same window and simulations, which is the SISMID comparison from the issue: two models with the same mean degree and mean partnership duration accumulate the same number of partners per node even when their momentary degree distributions look nothing alike. The `?plot.netdx` example does this with high- and low-concurrency models at 200 edges and a mean duration of 25. Over 250 steps, half the nodes in the high-concurrency model have no partner at any moment and a quarter have two, while most nodes in the low-concurrency model have exactly one, and both accumulate about 8.5 partners per node (mean 8.63 vs 8.49, median 9 vs 8).

Other arguments: `window` restricts the observation period, `maxdeg` collapses the tail of the axis into a `"maxdeg+"` category, `unique.partners` switches between distinct partners and distinct partnerships, and `method = "b"` draws bars instead of lines. Legends report the mean of each distribution, and the plotted distributions are returned invisibly.

One thing worth knowing that came out of building the example: enforcing monogamy with `constraints = ~bd(maxout = 1)` shifts the realized duration well off target (19 against a target of 25 in my test), so I used `concurrent` target statistics on both sides instead, where the duration diagnostics are clean.

Tests cover the two edgelist helpers against a hand-checked spell layout, `get_degree_dist()` against a direct tabulation of the edgelist, the argument validation, and the plot paths. `test-netdx.R` passes locally at 130 tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `805c0e91e01e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.