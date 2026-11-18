# Issue

**Title:** Re-activate pre-scoring = 1 if no reduction is used

## Description

This PR re-activates the pre-scoring default for unreduced sequences as stated in the help message (mainly important for nucleotide mode). Additionally, some minor fixes that have been already adjusted in lambda3 but were missing in lambda2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52fd0bb00f85`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.