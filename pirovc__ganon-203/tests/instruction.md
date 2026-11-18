# Issue

**Title:** Feature/ibf fp corr target

## Description

Introduce FPR correction ratio for targets split among bins. Max. correction ratio is simulated to define best bin length and real correction (usually smaller) ratio is calculated when building.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1ba004cd475`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.