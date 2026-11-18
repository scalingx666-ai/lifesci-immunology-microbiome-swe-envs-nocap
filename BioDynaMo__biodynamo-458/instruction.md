# Issue

**Title:** Fix DiffusionGrid::GetConcentration error label

## Description

## Summary
- The out-of-bounds error in `GetConcentration` incorrectly identifies itself as `ChangeConcentrationBy`, making it impossible to distinguish read vs write OOB errors when debugging.

## Test plan
- [ ] Existing unit tests pass (no behavioral change, label only)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67c8d6f3ac51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.