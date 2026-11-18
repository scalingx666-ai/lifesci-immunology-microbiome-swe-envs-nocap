# Issue

**Title:** Cleaner el cuml

## Description

put the `cumulative.edgelist` control check inside `update_cumulative_edgelist` to govern weather or not to update.

error if calling `get_cumulative_edgelist` and `cumulative.edgelist == FALSE`

This will catch all cases of trying to use cumulative edgelist when its not calculated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f86d111d32c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.