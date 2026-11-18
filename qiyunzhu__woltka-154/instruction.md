# Issue

**Title:** micro optimized gene coords

## Description

Changed `sorted` into `if` in ordered two numbers. This micro optimization notably increased the performance of the gene coordinates loading process.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7de19f87ede9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.