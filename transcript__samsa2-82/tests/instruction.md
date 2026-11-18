# Issue

**Title:** More flexible filename handling

## Description

This is a fix for  where `run_DESeq_stats.R` and `Subsystems_DESeq_stats.R` will fail if filenames do not follow the pattern `experimental_#_...` or `control_#_...`.

Rather than splitting the filenames by underscores, the new code removes `experimental_` or `control_` from the beginning and `.cleaned` from the end in order to get the sample names for matching.

Also, I solved the problem of R wanting to change the counts to factors by setting the sample names as row names before transposing. (Previously, if the sample names were not numeric, transposing the dataframe would create columns that were mixed so R would convert all columns to factors. Pulling the sample names into the row names before transposing allows them to directly become column names without affecting the data types.)

Thank you and let me know if you have any questions!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6dad883c5f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.