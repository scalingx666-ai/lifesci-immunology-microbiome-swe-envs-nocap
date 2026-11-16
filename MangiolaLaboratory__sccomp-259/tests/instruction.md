# Issue

**Title:** Modify significance statistic handling

## Description

- Incremented package version to 2.1.26.
- Changed default value of `significance_statistic` in plotting functions from "FDR" to "pH0" for improved clarity in significance interpretation.
- Updated documentation and function parameters to reflect the new default and ensure consistency across plotting functions.
- Enhanced user messaging to inform about the change in default significance statistic for boxplots.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e6368e3cf82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.