# Issue

**Title:** add option to set `constraint_fn` to a numeric, automatically choosing a single category constraint

## Description

Option to set `constraint_fn` to a single integer value, this will set a single category constraint with that integer as the index of the reference taxon.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f79e2c448d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.