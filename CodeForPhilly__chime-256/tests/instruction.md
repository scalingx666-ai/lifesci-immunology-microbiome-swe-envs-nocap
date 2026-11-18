# Issue

**Title:** Fix dispositions and census construction

## Description

Cleanup the dataframe construction.

Include day in dispositions_df.

Eliminate duplicated calculations in census_df.

Move calculations above model property setters for data science.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `330792c72950`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.