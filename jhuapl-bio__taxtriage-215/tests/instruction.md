# Issue

**Title:** fixing report histogram language, adding cross-sample fixes for gener…

## Description

- Adding multi-sample or cross-sample comparison table
- Updating genera comparison table to allow filtering of samples
- updating tab formatting
- Changes to exporting histogram (remove extra y axis)
- Adding compare coverages for cross-samples and detections

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4df207c025f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.