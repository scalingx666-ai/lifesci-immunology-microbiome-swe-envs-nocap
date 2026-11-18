# Issue

**Title:** Fix/alpha rarefaction bug

## Description

Fix getAlpha()/addAlpha() averaging only the first rarefaction round (#853)

.

With `niter > 1`, `.alpha_rarefaction()` `cbind()`s the per-round results into one matrix in which every round repeats the same column names. `res[, cname]` returns only the first matching column, so `rowMeans2()` averaged a single round and `getAlpha()`/`addAlpha()` returned the first rarefaction. Selecting the columns with `colnames(res) == cname` averages all rounds. Regression from 45b1d3ec (#669).

**Changes**
- `R/addAlpha.R`: one-line fix and a one-line comment.
- `tests/testthat/test-addAlpha.R`: new test that rarefies the same rounds with `rarefyAssay()` under the same `RNGseed` and checks that `getAlpha()` returns their mean. It uses `chao1`, so it also catches averaging the estimate and `_se` columns together, and it checks that the rounds differ, so the comparison cannot pass with identical rounds. It fails before the fix.
- `NEWS`, `DESCRIPTION`: entry and version bump to 1.21.12.

`test-addAlpha.R` passes locally (49 expectations, 0 failures).

Description generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b78e622540b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.