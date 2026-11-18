# Issue

**Title:** 143 host removal leads to mismatched read counts

## Description

- Fixed an issue where mismatched paired-end reads would lead to failures in denovo assembly (and cancelling of the given sample)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a245f945356c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.