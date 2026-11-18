# Issue

**Title:** Bugfix: Parse empty taxonomy as empty list

## Description

Previously, it got parsed as `[""]`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b5d46541cfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.