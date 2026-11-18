# Issue

**Title:** Bug fixes

## Description

Metadata handling if data is missing from the ENA API.
Don't run IQTree if there is less than 3 sequences.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c8d850d6b84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.