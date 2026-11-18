# Issue

**Title:** Correct zero-variance feature filtering

## Description

## Summary
- correct the zero-variance filter to use the untransformed SD threshold of zero
- clarify the histogram scale and counts-assay scope
- remove the unused threshold variable

## Validation
- `git diff --check`
- affected R chunks parse successfully

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c05bf46fd78`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.