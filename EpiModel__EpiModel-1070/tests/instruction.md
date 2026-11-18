# Issue

**Title:** Use the solved time vector in dcm methods

## Description

.

`control.dcm()` documents `nsteps` as either a scalar maximum or an explicit vector of times, and a model given a vector solves fine. Every downstream method then failed on it, all for the same reason: they treated `control$nsteps` as a scalar.

| call | before |
|---|---|
| `as.data.frame(mod)` | `'to' must be of length 1` |
| `plot(mod)` | `invalid 'xlim' value` |
| `summary(mod, at = 1)` | `'length = 4' in coercion to 'logical(1)'` |
| `comp_plot(mod, at = 1)` | `'length = 4' in coercion to 'logical(1)'` |

All four now take their time coordinates from `control$timesteps`, which `saveout.dcm()` fills with the times actually solved in both the scalar and vector cases.

I took the issue's recommendation to fix rather than restrict `nsteps` to a scalar, since non-integer `dt` is a supported feature and the vector form is documented. Say the word if you would rather narrow the input instead, it would be a docs-and-validation change on top of this.

Three decisions worth your eye:

- **`at` is now validated by membership**, not by range. A time between two solved times (`at = 2` when the model solved 0, 0.25, 1, 3) is rejected rather than silently returning an empty summary. The matching tolerates the floating point error of a non-integer `dt` sequence, so `at = 1.3` works under `dt = 0.1`, where the stored value is not exactly 1.3. This changes two existing error messages, so two tests are updated: `summary.dcm` and `comp_plot.dcm` now share the wording "Specify at as one of the time steps of the model, between X and Y".
- **Time step reporting.** `print()` printed the whole time vector under "No. time steps", and `summary()` printed a blank (it read `object$nsteps`, which does not exist on a `dcm`). Both now report the number of times solved, adding the range when those times are not 1..n, so `dt = 0.1` over 3 steps reads `21 (1 to 3)` rather than `3`. Output is unchanged for a standard model.
- **Plot limits** come from `range(c(0, timesteps))`, which keeps the existing `c(0, nsteps)` behavior for standard models rather than re-basing every existing plot at 1.

Also fixed while testing the run selection the issue asked about: `as.data.frame.dcm` keyed its first-block test on `j == min(run)` rather than on the first iteration, so `run = c(3, 1)` errored with "numbers of columns of arguments do not match" and `run = c(2, 2)` silently returned one copy. Runs now come back once per request, in the order requested.

One unrelated line: `.gitignore` gains `/Rplots.pdf`, matching the existing `tests/testthat/Rplots.pdf` entry, since plotting from `Rscript` at the repo root drops one there.

Tests: new coverage for a nonuniform time vector, a non-integer `dt` including the off-grid and out-of-range rejections, and run ordering. `test-dcm.R` (94), `test-dcm-long.R` (116), `test-plot-dcm.R` (14), `test-comp-plot.R` (19), `test-print.R` (48), `test-mutate.R` (12), and `test-truncate-restart.R` (26) all pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd831f8804bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.