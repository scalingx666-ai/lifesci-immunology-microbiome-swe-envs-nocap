# Issue

**Title:** Use locality-sensitive hashing to reduce space of candidate probes

## Description

A user can invoke LSH as one of two optional arguments provided to the executable. This can provide significant reductions in runtime and memory requirements, particularly when the input consists of a large number of highly similar sequences.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7f927763ce6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.