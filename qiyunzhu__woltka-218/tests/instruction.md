# Issue

**Title:** Improved file parsing mechanism

## Description

Previously the program runs without waiting for the subprocess to complete. Now it does.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71adc8a9a64c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.