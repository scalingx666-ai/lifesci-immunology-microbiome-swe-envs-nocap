# Issue

**Title:** fix empty bin_info.tsv with --skip-abundances

## Description

My bad. Inner join removes all the other bin info...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37bd15b229ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.