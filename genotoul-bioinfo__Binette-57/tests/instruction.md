# Issue

**Title:** Sort bins to make Binette reproductible

## Description

Small change in the code to sort bins when creating intermediate bins to ensure they have a consistent ids across executions to prevent output from changing between different executions.
Should fix issue #54

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af59facdb432`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.