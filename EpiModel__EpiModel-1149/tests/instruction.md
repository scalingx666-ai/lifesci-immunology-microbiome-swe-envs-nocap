# Issue

**Title:** control.net(.timing = TRUE): record the time of each module as epi outputs

## Description

- Now: to see where a `netsim()` step spends its time we wrap each module by hand in a session, and every project does it its own way.
- Goal: a run that reports its own time per module, in a form the existing tools already handle. This is the first piece of the harness in EpiModel/EpiModelHIV-p#428.
- How: `control.net(.timing = TRUE)` records each module's wall-clock time and CPU time at each step as epi outputs, `timing.<module>` and `timing.cpu.<module>`, plus `timing.step` and `timing.cpu.step` for the whole step. They are ordinary epi trackers, as you asked on the issue, so `as.data.frame()`, merges and the HPC tibbles carry them with no new code. It is off by default, and no clock is read when it is off.
- Review: both. The change is about 25 lines in `netsim_run_modules()`. Is `.timing` the right name and place for it, and do you want `timing.step`?

### Details

- The control goes through `...` and defaults to `FALSE` in `netsim_validate_control()`, the way `.traceback.on.error` does. It has a "Module Timing" section in `?control.net`.
- The names are the module names as `module.order` spells them: `timing.resim_nets.FUN`, `timing.infection.FUN`.
- `timing.step` also covers what runs outside the module loop (updaters, attribute and epi trackers, `verbose.FUN`), so it is a little larger than the sum of the module columns.
- Times are in seconds. The wall-clock time is from `Sys.time()`, because `proc.time()` rounds to the millisecond, which is too coarse for a module that takes 0.1 ms. The CPU time is user plus system from `proc.time()`, read before and after each module (added after review). It is rounded the same way, so it reads as a mean over many steps. `system.time()` would do the same with `gcFirst = FALSE`; with its default it runs a full `gc()` before every module.
- The first time step is `NA`: it is the initialization and no module runs.

### Checks

- New `test-netsim-timing.R`: one wall-clock and one CPU column per module and for the step, no negative values, the modules never summing to more than the step, every other column of `as.data.frame(sim)` identical to an untimed run under the same seed, no timing column when off, and a module added through `module.order` timed under its own name.
- Eight seeded built-in models with the control off give the same output as `main` (`c665760f`): `as.data.frame(sim)`, `get_nwstats()`, the transmission matrix, the cumulative edgelist and, for full networks, the edge spells. With it on they match once the timing columns are dropped.
- Full suite with the long tests: 4,976 expectations, no failures. Lint is clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f0e4b23a8eda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.