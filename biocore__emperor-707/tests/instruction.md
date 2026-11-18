# Issue

**Title:** BUG: Fix problem with two-dimensional data

## Description

If the plot was initialized with two dimensions, the UI would fail to
instantiate as several objects had the dimensions hard-coded. I've
changed this to make it dependant on the data. In addition the Python
API will now check for one-dimensional data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a6338ede8c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.