# Issue

**Title:** Fix typo of color to describe quality plots

## Description

The hexcode 66C2A5 is used to represent the mean, which is green (see
https://github.com/benjjneb/dada2/blob/master/R/plot-methods.R#L198).

Rest of documentation is consistent
https://github.com/benjjneb/dada2/blob/master/R/plot-methods.R#L125.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cf7a1811c3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.