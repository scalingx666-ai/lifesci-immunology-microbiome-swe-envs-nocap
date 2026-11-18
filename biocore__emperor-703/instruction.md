# Issue

**Title:** BUG: Fix a problem with no metadata columns

## Description

Fixes a problem where passing a dataframe with no metadata columns would
lead to a failure in the UI. The problem originated from the way we were
using the apply function to transform the values to strings, and how we
were merging the index's names.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `097b6542fa7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.