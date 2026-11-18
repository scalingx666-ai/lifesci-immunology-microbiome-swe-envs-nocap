# Issue

**Title:** Per-simulation follow-ups to #1087

## Description

Stacked on #1007: this merges into `dev` and ships with #1007 in v2.7.0.

Replaces #1072, most of which #1087 already covered. Finishes #1059, which #1007 will close when it merges.

What #1087 left:

- Open-population tests for `get_sims()`, `merge()`, `make_restart_point()` and restart. The #1087 tests use `d.rate = 0`, so `coef.form` is the same in every sim and a misalignment can't show up. The new tests fail on the July base of #1072 and pass here.
- `merge()` keeps the `transmat` class on `stats$transmat`, so splitting with `get_sims()` and merging back returns the original object.
- `get_sims()` gives a clear error for `sims` values of 0, negative, non-integer or `NA`, instead of an unrelated `names` error.

Three gaps neither #1087 nor #1072 covered, found in EpiModelHIV-p runs:

- `merge()` now skips the controls for how a run was executed rather than what it simulated (`ncores`, `verbose`, `verbose.int`, and the checkpoint settings). Since `netsim()` forces `ncores = 1` for a single sim and turns `verbose` off for several, a 1-sim batch couldn't be merged with a multi-core batch.
- `truncate_sim()` now cuts `nwstats` along with `epi`. It kept every row, so `get_nwstats()` failed on the result. With `reset.time = TRUE` it also shifts the `transmat` and `raw.records` times, as #1007 already does for `attr.history` and the cumulative edgelist. `make_restart_point()` now stops on a truncated object, since its `run` is still on the original time steps and the time attributes were re-based by the wrong offset.
- `get_sims()` keeps `nwparam[[n]]$coef.form` in step with the first sim it returns. It was always sim 1's, so a restart point made with `sim_num = 2` disagreed with its own `coef.form`. Restarts were not affected, since they read `coef.form`.

The time labels of a truncated object with `reset.time = FALSE`, and of resumed runs, are left to #1085.

Testing:

`R CMD check --as-cran` is clean apart from a `.git` note from building in a worktree. With `NOT_CRAN=true`, test-get, test-merge, test-truncate-restart, test-tracked-attrs, test-netclique, test-multinets and test-cumulative_edgelist all pass. The new tests fail on plain `dev`.

I also ran EpiModelHIV-p v3.3.x (10k nodes, 156 steps, Template settings) against main, dev and this branch. The runs covered multi-sim calibration runs, restart points from sim 2 via `make_restart_point_hiv()` restarted through `reinit_msm` into a scenario, second-generation restarts, `get_sims()`, split-then-merge round trips, and merges of runs from separate `control_msm()` calls. Restarts and slot alignment pass on all three. The merge and truncate checks that fail on main and dev (11 of them) all pass here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c585c310e58c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.