# Issue

**Title:** fix: ValueError: cannot insert Country, already exists

## Description

## Related issues
fix #1821

## What was changed
Fix `ValueError`: cannot insert Country, already exists.

## Summary by Sourcery

Bug Fixes:
- Modify the resampling method to handle potential duplicate 'Country' column during DataFrame reset, preventing insertion errors

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b11b7a8a35c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.