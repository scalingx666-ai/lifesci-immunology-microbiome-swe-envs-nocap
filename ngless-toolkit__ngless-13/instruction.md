# Issue

**Title:** Use larger blocksize with bwa index on >100MB files

## Description

This reduces CPU time required for indexing drastically at the expense of higher memory usage.

The same machine that will run `bwa mem` should be able to accommodate this without problems.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91c99ced64bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.