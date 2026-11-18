# Issue

**Title:** Apply sims to means and quantiles in plot.icm and plot_netsim_epi

## Description

.

Going with option 1 from the issue: `sims` selects the simulations the plot is about, so the aggregates are computed over that subset. It matches the documented "a vector of simulation numbers to plot" and makes the mean line agree with the lines drawn beside it.

`draw_means()` and `draw_qnts()` take no `sims` argument and computed over the full `x$epi` matrix, so only the individual lines were ever filtered. In a four-simulation ICM with `i.num` of 34, 47, 47, 51 at a time step, `plot(m, y = "i.num", sims = 1:2)` drew its mean at 44.75 while the two plotted lines average 40.5.

The fix restricts the epi output to the selected simulations once, up front, through a shared helper in `R/plot.R`, so everything downstream is drawn from the same data rather than threading `sims` through each drawing function. `control$nsims` is updated with it, which also gets the dependent defaults right: selecting a single simulation now draws no quantile band, since one simulation has no spread, and the line transparency scales to the subset.

Both plot paths take the same three lines, keeping them symmetric per the note in CLAUDE.md. `plot.epi.data.frame()` inherits it through `plot_netsim_epi()`. `plot(type = "network")` and `plot(type = "formation")` are untouched, as they handle `sims` separately.

Two smaller notes:

- The `sims` guard now rejects values below 1. Previously `sims = 0` produced an empty selection and a confusing downstream failure rather than an error.
- This is a user-visible change for anyone passing `sims`, so it is filed under BREAKING CHANGES in NEWS with the before/after numbers.

Tests: a new `test-plot-sims.R` runs the same assertions against both `plot.icm` and `plot.netsim`, capturing what is drawn by mocking `lines()` and `polygon()` in the package namespace (the pattern already used in `test-netdx.R`). It covers the mean line for a subset, for the default, and for a single simulation; the quantile band against a directly computed `quantile()`; the absence of a band for one simulation; the identity of the individual lines; the argument guards; and the `plot.epi.data.frame` path. 27 assertions, plus clean runs of `test-icm.R`, `test-icm-long.R` (271), `test-netsim.R` (86), `test-plot-epi-dataframe.R`, `test-comp-plot.R`, and `test-net-long.R` (141).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `add364d15066`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.