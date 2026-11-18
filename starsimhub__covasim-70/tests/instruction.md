# Issue

**Title:** Dynamic resampling

## Description

Closes: 

As discussed in issue, this change halves non-susceptible population whenever we reach midpoint of population, until we reach desired population size.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2fd4869bf459`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.