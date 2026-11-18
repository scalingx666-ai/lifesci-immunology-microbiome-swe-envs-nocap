# Issue

**Title:** ENH: Add exceptions and tests for missing samples

## Description

Two cases are now explicitly checked for:

1) None of the samples in the ordination are part of the metadata.

2) Some samples in the coordinates matrix are not part of the metadata.
In this case the error can be overridden with the ingore_missing_samples
argument.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d69390d0baf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.