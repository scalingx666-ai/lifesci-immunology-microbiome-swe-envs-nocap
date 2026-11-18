# Issue

**Title:** Speed up DRAM annotations

## Description

Use `simplejob_threads` for rule DRAM_annotate. Addresses #533 .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1c4764963bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.