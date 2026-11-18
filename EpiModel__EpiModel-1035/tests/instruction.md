# Issue

**Title:** swap head / tail storage

## Description

Fix #1021
Correctly record `head` and `tail`. Previously it inverted them as `el[, 1]` is tail in (t)ergm outputs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `069cd8ad9b4a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.