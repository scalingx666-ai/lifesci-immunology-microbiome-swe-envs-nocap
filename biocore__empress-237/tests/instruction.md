# Issue

**Title:** Match feature table and ordination

## Description

This would otherwise lead to situations where mismatching categories
would be displayed in the ordination and phylogeny. In principle users
should use the rarefied table that was used for generating the
ordination i.e. samples should have a 1:1 match.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8d1a06a1179`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.