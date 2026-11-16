# Issue

**Title:** Enhance sccomp_predict and summary_to_tibble functions to support rob…

## Description

…ust statistics

- Added a new parameter `robust` to `sccomp_predict` and `summary_to_tibble` functions to allow users to choose between classical and robust statistics for summary calculations.
- Updated documentation to reflect the new `robust` parameter and its implications on the output.
- Modified the prediction logic to return median and median absolute deviation when `robust` is set to TRUE.
- Added tests to ensure robust predictions return expected columns and values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dcc5b0e22658`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.