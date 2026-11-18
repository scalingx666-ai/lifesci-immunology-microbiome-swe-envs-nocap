# Issue

**Title:** Server queries in multi-graph regime with full loading to RAM

## Description

Support requests with flag `"in_ram": true`, which means the graph would be fully loaded to RAM before querying.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06e4862edfae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.