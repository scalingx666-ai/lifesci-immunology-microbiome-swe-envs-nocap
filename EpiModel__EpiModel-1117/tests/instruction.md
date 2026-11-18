# Issue

**Title:** Fix the guards for argument names removed in 2.6.1

## Description

.

The `.m2` guards matched anywhere in a name: `param.net()` used `grep(".m2", ...)` with an unescaped dot and `init.net()` used `grep("m2", ...)`, so names like `area.km2` or `sim2` were refused. A new `check_m2_suffix()` matches the suffix only, and the param and init constructors of all three classes now call it (ICM and DCM had no `.m2` guard).

`b.rate` has had no guard since #1013, which assumed `...` would give an unused-argument error. It doesn't, so `b.rate` was stored and the model failed later. A new `check_removed_params()` refuses `b.rate`, `trans.rate` and their `.g2` forms, called from `crosscheck.icm()`, the built-in branch of `crosscheck.dcm()`, and the built-in branch of `crosscheck.net()` (which checked neither). I put it in crosscheck rather than in `param.*()` because that's where the old `trans.rate` checks lived for DCM and netsim: extension models (custom DCMs, `type = NULL` netsim) can still use these names for their own parameters. EpiModelHIV's old heterosexual model has a `b.rate`, for one. If you'd rather refuse them everywhere, it's a one-line move into the constructors.

Tests in `test-net-inputs-validation.R` cover the suffix match in every class and the `b.rate`/`trans.rate` errors for ICM, DCM, and netsim, plus an extension netsim run that accepts `b.rate`. They fail on main.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ada72cf1de6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.