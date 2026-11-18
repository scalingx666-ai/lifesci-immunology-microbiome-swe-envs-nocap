# Issue

**Title:** Fix phyloseq converter

## Description

Related to this issue: 

In the old version, some phyloseq-specific attributes were still included in the matrix which failed the methods.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2d09f6ed8bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.