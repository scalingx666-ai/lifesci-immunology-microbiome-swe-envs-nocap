# Issue

**Title:** Select timepoints in mcar_test and explain undefined Little's tests

## Description

ep.pp.mcar_test tests 3D data at the timepoints selected by tem_names, reduced by agg like in filter_observations, and raises an error naming the variables that are not observed together in at least two observations instead of silently returning NaN for Little's test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0655a5b94b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.