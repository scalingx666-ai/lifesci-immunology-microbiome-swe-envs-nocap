# Issue

**Title:** correction of double counting reads

## Description

reformat counts gives the sum of R1 and R2 reads.
For me it makes less sens to count them both.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `284be66ed1e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.