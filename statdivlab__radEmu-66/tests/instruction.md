# Issue

**Title:** add check to `emuFit()` to throw an error for a category with only zero counts across samples

## Description

add check to `emuFit()` to throw an error if any columns of `Y` (representing categories) have 0 counts for all samples. Add test of this functionality.

Files that are changed:

- "emuFit.R" now adds this check and throws an error if needed
- "test-emuFit.R" now has a test of this functionality

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b38c736ef02`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.