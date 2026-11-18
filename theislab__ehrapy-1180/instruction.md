# Issue

**Title:** Compute log fold changes of categorical features in rank_features_groups

## Description

`ep.tl.rank_features_groups` reports the log2 ratio of the fractions of observations with value 1 as log fold change of binary categorical features, and NaN for categorical features with more levels, instead of 1 regardless of direction. Features of all tests stay ordered by adjusted p-value, now with ties broken by p-value, which the docstring states, so g-test and t-test scores are never compared.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5b2df73689a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.