# Issue

**Title:** new parameter: --tie-ratio

## Description

When the best species score is A.
Scores >= (A * --tie-ratio) are considered as ties to the best score.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b60d8143112`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.