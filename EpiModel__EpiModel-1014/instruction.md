# Issue

**Title:** Fix inconsistencies between plot.netsim stats and plot.netdx

## Description

## Summary

.

- Extract duplicated stats validation logic (find available stats, validate user's `stats` argument, subset data, pull targets) from `plot_netsim_stats()` and `plot.netdx()` into a shared `validate_stats_selection()` helper in `R/plot.stat_table.R`
- Add `xlim`, `xlab`, `ylim`, `ylab` parameters to `plot.netdx()` and pass them through to `plot_stats_table()`, matching the interface already available via `plot.netsim(type = "formation")`
- `dynamic` parameter handling left as-is — both sides are correct (`plot.netdx` reads from the object, `plot_netsim_stats` hardcodes `TRUE` since netsim is always dynamic)

## Test plan

- [x] `R CMD check` passes
- [x] `plot(dx, type = "formation", xlim = ..., ylim = ..., xlab = ..., ylab = ...)` works on a `netdx` object
- [x] `plot(sim, type = "formation")` on a `netsim` object still works identically

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `35dbba5beca5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.