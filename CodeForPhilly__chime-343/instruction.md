# Issue

**Title:** [dash] Remove Penn hospital references from visualizations

## Description

Issue #316 Removed references to Penn hospital from template. It may be possible to add a way to customize the hospital, but that might be worth it only if doing so would yield different data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0afcecdadf13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.