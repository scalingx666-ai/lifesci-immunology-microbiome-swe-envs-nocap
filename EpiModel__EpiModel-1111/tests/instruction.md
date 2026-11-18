# Issue

**Title:** Add ode.args and solver hooks to control.dcm

## Description

Small additions to the DCM class for 2.7.0, so that extension packages can run larger ODE models through `dcm()` and return a standard `dcm` object. The first user will be EpiModelHIVdcm, the compartmental HIV model for the AIDSVu project.

- `control.dcm(ode.args = )`: a named list passed on to `deSolve::ode()` or `dede()` (tolerances, `hmax`, and so on). Arguments `dcm()` sets itself are refused.
- `control.dcm(solver = )`: a function `(y, times, func, parms, control)` that replaces the `ode()` call, for example to restart the solver at abrupt rate changes. Extra columns it returns are kept as outputs, and `.flow` columns are differenced as before.
- `print.dcm()` printed list parameters with `cat()` and failed; it now uses `format_param()` and lists only the first 20 initial conditions and outputs of larger models.
- `plot.dcm()` started the x-axis at 0 even for calendar-time models (2010 to 2037); it now keeps the origin only when times start between 0 and 1.

All defaults reproduce current behavior. New tests in `test-dcm.R` cover each change. The dcm, print, and plot test files pass with `NOT_CRAN=true`, and `R CMD check --no-manual --ignore-vignettes` is clean. I also checked the solver hook against the AIDSVu v3 model: with its piecewise solver plugged in, `dcm()` reproduces the model's own run exactly, while a single `ode45` solve across the rate breaks is off by up to 0.07%.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8e7ec5312f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.