# Issue

**Title:** fix: remove duplicate builtin: prefix in 10x-sc-5gex-gemx-v3 whitelist

## Description

The CELL whitelist address had a double "builtin:" prefix which caused an IllegalArgumentException when running refineTagsAndSort.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d930d5a38b02`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.