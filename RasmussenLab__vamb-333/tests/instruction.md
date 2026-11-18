# Issue

**Title:** Switch to strobealign --aemb as default abundance estimator

## Description

* Add `Abundance.from_aemb` function
* Add `--aemb` flag on command line, similar to `--bamdir`
* Update README and elsewhere that we recommend using strobealign --aemb

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `640c37f619be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.