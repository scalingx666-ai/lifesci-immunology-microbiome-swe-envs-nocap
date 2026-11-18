# Issue

**Title:** Bootstrap the signed subgroup difference in evaluate

## Description

The confidence interval of the subgroup difference of ep.ml.evaluate now resamples the signed difference between the subgroups with the highest and lowest value instead of the largest difference of every bootstrap sample, which could never be negative. Intervals now include 0 when subgroups do not differ, while the point estimates stay the same.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bac1cc3a163f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.