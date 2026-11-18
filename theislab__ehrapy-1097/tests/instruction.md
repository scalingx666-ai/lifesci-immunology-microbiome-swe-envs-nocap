# Issue

**Title:** Remove `mice_forest_impute` and drop the `miceforest` dependency

## Description

## Why

`miceforest` is effectively unmaintained and is now broken against current `lightgbm`.
Removing it is easiest.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76a9687c62b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.