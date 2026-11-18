# Issue

**Title:** update to v3.4.2

## Description

**fix:** preventing logical error in prophage pruning when leading 5kb chunk does not contain genes #6 

**change:** modifying pyhmmer runner to spawn no more than 4 threadpools. This increases performance and, on compute nodes with many CPUs, drastically lowers memory footprint.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa6f2f77bc1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.