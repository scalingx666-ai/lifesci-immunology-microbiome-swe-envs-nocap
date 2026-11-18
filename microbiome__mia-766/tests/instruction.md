# Issue

**Title:** Add inverse rank normalisation (invnorm) to transformAssay

## Description

Adds inverse rank normalisation to transformAssay as method = "invnorm". Ranks values per sample/feature and maps them to standard normal quantiles.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85f5c2fc6b70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.