# Issue

**Title:** Implement sensitivity analysis on initial conditions for DCM models

## Description

## Summary
- Extends DCM sensitivity analysis to support vector-valued initial conditions in `init.dcm()`, mirroring the existing parameter sensitivity analysis in `param.dcm()`
- Passing a vector (e.g., `i.num = c(1, 5, 10)`) now produces one model run per element, just like vector-valued parameters
- Vectors can be used in both `param.dcm()` and `init.dcm()` simultaneously (all vectors must have the same length)

## Example

```r
# Varying initial conditions only
param <- param.dcm(inf.prob = 0.2, act.rate = 0.25)
init <- init.dcm(s.num = 500, i.num = c(1, 5, 25))
control <- control.dcm(type = "SI", nsteps = 500)
mod <- dcm(param, init, control)
plot(mod)

# Varying both parameters and initial conditions
param <- param.dcm(inf.prob = c(0.1, 0.2, 0.3), act.rate = 0.25, rec.rate = 1/50)
init <- init.dcm(s.num = c(500, 400, 300), i.num = c(1, 5, 10), r.num = 0)
control <- control.dcm(type = "SIR", nsteps = 500)
mod <- dcm(param, init, control)
plot(mod)
```

## Changes

- **`R/dcm.R`**: `nruns` now computed from both parameter and initial condition vector lengths; `t0` constructed per-run inside the loop; validation that all varying vectors have the same length; `init` stored in output object; added roxygen example
- **`R/dcm.inputs.R`**: Added `Sensitivity Analyses` section to `init.dcm()` docs; updated `sens.param` description in `control.dcm()` to cover both parameters and initial conditions
- **`R/print.R`**: `print.dcm()` now displays initial conditions (filtering out internal flow variables)
- **`tests/testthat/test-dcm.R`**: 7 new tests (varying init only, varying both, mismatched lengths, custom models, as.data.frame, print)
- **`man/`**: Regenerated from roxygen

## Test plan
- [x] All 60 DCM tests pass (43 existing + 7 new)
- [ ] Full `R CMD check` via CI

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed1fd04335cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.