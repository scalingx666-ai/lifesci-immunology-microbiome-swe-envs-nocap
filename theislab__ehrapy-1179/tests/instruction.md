# Issue

**Title:** Test variables with missing values on their observed values in rank_features_groups

## Description

`ep.tl.rank_features_groups` tests numeric variables with missing values on their observed values in every group, and computes their log fold changes from them, instead of reporting a score of 0 and a p-value of 1 for any variable with a single missing value. Variables without enough observed values in a compared group to test are named in a warning.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59bb1c584b49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.