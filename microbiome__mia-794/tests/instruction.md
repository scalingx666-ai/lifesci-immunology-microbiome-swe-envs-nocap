# Issue

**Title:** Default getMDS and addMDS to no feature filtering (ntop = Inf)

## Description

### Summary of Changes

- Set `ntop = Inf` by default in `mia::getMDS` and `mia::addMDS` so that all features are retained before running MDS, avoiding unintended feature filtering in the microbiome context (unlike `scater::calculateMDS` which defaults to `ntop = 500`).
- Updated documentation in `R/getMDS.R` and `man/addMDS.Rd` describing feature retention and how to supply a finite `ntop` or `subset.row` if feature filtering is desired.
- Updated unit tests in `tests/testthat/test-addMDS.R`.

Relates to microbiome/OMA#824.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d5eb16a8491`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.