# Issue

**Title:** Fixes two subject / state error

## Description

There is a bug in the rank estimation when the minimum shape of the input table is less than 3. See issue #38 & #39.

This PR fixes that bug by not estimating a table rank with less than 3 samples. Also, added additional tests to ensure two-state/subject does not break tensor factorization in the future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c419b0392e87`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.