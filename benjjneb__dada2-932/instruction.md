# Issue

**Title:** mergeSequenceTables says what's wrong when stopping

## Description

I've had the error that "At least two valid sequence tables, and no invalid objects, are expected." when running the function on contents of a folder. I didn't know which of the ~600 tables is wrong, and to find out that it was `553_featureTable.rds`, I needed to do a bit of digging: find where the error comes from, open the R session with `is.sequence.table` , etc.

If the error message says what the problem is, it might save the user a bit of time.

Same rationale for duplicate sample names.

Also adds a check for the case of less than two tables passed in.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9d25c77ddcd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.