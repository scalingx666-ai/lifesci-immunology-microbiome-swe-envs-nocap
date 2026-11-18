# Issue

**Title:** Fix alpha rarefaction

## Description

Rarefaction in alpha diversity calculation did not work, because the function failed to match samples. The matching is done because rarefaction can drop some samples. It is done based on sample names, however, sample names were not added to results which caused the function to fail.; it returned only NAs because it did not find any matches.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41a35253613b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.