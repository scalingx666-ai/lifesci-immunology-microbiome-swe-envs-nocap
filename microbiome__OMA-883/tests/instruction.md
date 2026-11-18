# Issue

**Title:** Document addMDS rarefaction feature retention

## Description

## Summary
- retain all features when rarefying in the addMDS example
- explain the interaction between `ntop` and rarefaction depth

## Validation
- `git diff --check`
- affected R chunk parses successfully

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bd6fbce16f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.