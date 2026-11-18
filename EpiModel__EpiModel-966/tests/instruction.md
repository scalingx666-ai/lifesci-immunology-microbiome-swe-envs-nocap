# Issue

**Title:** Augment `trim_netest` to also remove summary

## Description

`trim_netest` is meant to strip `netest` object of all but the bare minimum to run simulations.

I realized that `netest` was storing the result of `summary(fit, ...)` in `netest$summary`. This single entry was taking up to ~900MB on some HIV models.

Removing it massively reduces the size of the final files and the amount of data to pass to parallel workers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c55e16de05ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.