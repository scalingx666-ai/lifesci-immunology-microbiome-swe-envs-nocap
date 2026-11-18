# Issue

**Title:** Always remove temporary VCF files

## Description

This is a simple fix to always remove the temporary VCF files that are created by the thread workers. 

As well as a small typo fix in the readme.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `424b21ad5bd8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.