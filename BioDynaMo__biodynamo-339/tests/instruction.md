# Issue

**Title:** Remove `RungeKuttaGrid`

## Description

As discussed in previous meetings, the RK implementation is not tested properly and not maintained. To avoid unexpected results for users, we remove it here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e327e53c4bec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.