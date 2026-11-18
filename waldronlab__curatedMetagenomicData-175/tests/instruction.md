# Issue

**Title:** Add actions to update and test combined_metadata.rda

## Description

Creates an action to generate combined_metadata.rda from curatedMetagenomicDataCuration and test it. Automatically creates a PR with the new file weekly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8097b8ad45ad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.