# Issue

**Title:** Fix read length plotting in aggregate mode

## Description

Small fix to the calculation of read counts that pass each length when being plotted in aggregate mode. `Cum=10*as.vector(cums)/rc` references the read count from the last sample processed, should be the sum of the actual read counts used in the tabulation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a661df1704d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.