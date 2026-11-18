# Issue

**Title:** fix plot axes

## Description

Final summary plotting script now takes completeness & contamination parameters to scale figure axes appropriately (previously fixed at 70 completeness and 10 contamination).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a4a135639a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.