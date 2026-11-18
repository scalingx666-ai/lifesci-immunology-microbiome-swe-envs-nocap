# Issue

**Title:** Updating aragorn flags to match prokka

## Description

Aragorn flags were updated to avoid reporting introns, which was producing 1-nt tRNA when parsing coordinates

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f638d10275c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.