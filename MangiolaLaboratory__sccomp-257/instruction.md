# Issue

**Title:** Refactor sccomp_boxplot function and enhance tests for factor handling

## Description

- Simplified the calculation of the 'is_zero' column in the sccomp_boxplot function by removing unnecessary lines.
- Updated the ggplot data handling to ensure parameter-level statistics are used as default for user-added layers.
- Added a new test case to verify that point counts match sample counts for factors with more than two levels, addressing issue #256.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b98046a6af2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.