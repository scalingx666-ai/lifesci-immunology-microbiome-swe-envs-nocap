# Issue

**Title:** Remove bad marker genes

## Description

Experiments on downloaded genomes found that 2/3rds of duplicated SCGs were one of the three removed here.
Removing these SCGs will significantly improve the accuracy of SCG usage.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `adbf338ec918`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.