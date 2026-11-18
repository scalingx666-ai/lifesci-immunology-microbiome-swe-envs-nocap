# Issue

**Title:** Fix for insert size distributions

## Description

I identified one issue with the insert size distribution: the template length was capped at 500, du to bowtie2 only reporting concordant pairs with TLEN < 500 (`-X` option in bowtie2)

This PR changes the model building process to iterate over all pairs instead of all concordant pairs, and adds some filters to the template length distribution to remove outliers.

The pre-built models will need to be rebuilt with these changes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b818bbcd7230`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.