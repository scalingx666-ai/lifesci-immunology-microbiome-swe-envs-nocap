# Issue

**Title:** [FIX] forgot to include search config in search ^^

## Description

when comparing dna searches between lambda2 and lambda3, don't forget to add `--adaptive-seeding 0 --seed-half-exact 0` as both are not yet supported on lambda3.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8dda56c03dd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.