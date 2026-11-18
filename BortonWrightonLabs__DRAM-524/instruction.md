# Issue

**Title:** fix: update diamond to fix hang problem

## Description

Update rundbcan easysubstrate and pin diamond to 2.2.5. In diamond 2.2.3 they mention fixing a problem with hanging sometimes, pinning diamond above that seems to eliminate the occassional dbcan hang problem.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05640dea9143`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.