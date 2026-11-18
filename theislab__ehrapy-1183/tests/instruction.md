# Issue

**Title:** Name the estimand in the summary of causal estimates

## Description

`CausalEstimate` records its `estimand` and `summary()` prints it, so propensity score matching with `target="att"` reports an ATT instead of mislabelling it as an ATE.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6b648c6eea6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.