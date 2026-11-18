# Issue

**Title:** Let every macOS CI matrix job finish after a failure

## Description

Disable fail-fast in the macOS unit and system CI matrices so a failure on one runner does not cancel results from the others. Keep the operating-system matrices and test commands unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48425dc13234`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.