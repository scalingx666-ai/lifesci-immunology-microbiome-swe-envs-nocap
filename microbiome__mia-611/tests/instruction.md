# Issue

**Title:** Fix pseudocount

## Description

Pseudocount was set to half of the minimum value by default. However, usually pseudocount is 1 when the matrix contains counts.

Now pseudocount is minimum value when counts, otherwise half of the minimum value

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5dc047897c35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.