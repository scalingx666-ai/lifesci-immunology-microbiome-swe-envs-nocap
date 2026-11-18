# Issue

**Title:** Document swapping alternative experiments

## Description

## Summary
- document promoting an alternative experiment with `swapAltExp()`
- show how to restore the original main experiment without data loss

## Validation
- `git diff --check`
- affected R chunk parses successfully
- verified swap and restore round trip with SingleCellExperiment

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bcc80a289dd9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.