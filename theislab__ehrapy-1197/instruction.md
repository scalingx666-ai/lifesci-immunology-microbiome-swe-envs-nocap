# Issue

**Title:** Put the subgroup difference on its own title line in subgroup_performance

## Description

ep.pl.subgroup_performance puts the difference between subgroups on a second line of every panel title. Titles of long metric names such as calibration_intercept are no longer cut off at the default width.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bac1cc3a163f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.