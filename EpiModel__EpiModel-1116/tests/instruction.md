# Issue

**Title:** Stop trim_netest() from modifying the object passed to it

## Description

.

With `nested.edapprox = FALSE` or `edapprox = FALSE`, `trim_netest()` assigned the trimmed formulas into `environment(object$formation)` or `environment(object$formula)`. That environment is shared with the object passed in, so `tr <- trim_netest(est)` also trimmed `est`, which then failed in `netsim()` when its formula referred to an object in that environment. It now gives the formula a copy of its environment first and assigns into the copy.

Tests in `test-netest.R`: a new one fits the issue's `nested.edapprox = FALSE` model with `levels = lv`, trims it, and checks that the original is unchanged and still runs in `netsim()` while the trimmed one fails on `lv` as documented. The Full STERGM test also checks that trimming leaves the original's `formula` environment alone. Both fail on main.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4dc39b112150`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.