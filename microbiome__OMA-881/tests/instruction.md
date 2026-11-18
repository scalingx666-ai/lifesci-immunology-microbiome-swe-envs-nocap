# Issue

**Title:** Use scaled fitted values for DMM drivers

## Description

## Summary
- select the best DMM model from metadata
- use the public scaled fitted values for loading visualization

## Validation
- `git diff --check`
- affected R chunk parses successfully
- full execution unavailable because of a pre-existing local readr ABI mismatch

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7bd2fc8e6da9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.