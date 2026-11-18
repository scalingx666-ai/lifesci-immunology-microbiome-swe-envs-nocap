# Issue

**Title:** Increase base vamb runtime to 48h

## Description

While we are making some changes, VAMB nearly always takes longer than 24h to run with 16 threads.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb474cbcee7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.