# Issue

**Title:** Exact w-shingling

## Description

Adds _--wj-exact_ command-line option for using exact weighted-jaccard shingling in sketching and comparison modes. Better parallelizes compilation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba57087d1d49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.