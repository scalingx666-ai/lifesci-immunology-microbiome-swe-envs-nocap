# Issue

**Title:** Hide progress bar when building query graph

## Description

* Disable progress bar in batch query (when extracting contigs from the query graph)
* Also print the number of k-mer matches and annotation rows in logs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9008b73c0681`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.