# Issue

**Title:** remove only empty rank cols

## Description

ping #568 
This PR modifies .remove_NA_cols_from_rowdata to remove only rank  columns with only NAs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9546b5568051`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.