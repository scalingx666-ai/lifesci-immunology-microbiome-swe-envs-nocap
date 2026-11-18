# Issue

**Title:** Replace lengths of stay with days

## Description

Clusters all days widgets together:
- Infectious Days
- Hospital Length of Stay (days)
- Days in ICU
- Days on Ventilator

Then the percent widgets afterward.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba27cab0277e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.