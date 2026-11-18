# Issue

**Title:** BUG: Sort unique metadata categories

## Description

Fixes a problem where metadata categories would appear to be ordered
randomly. Unique values are now sorted first alphabetically and then
numerically, mimicking the behaviour of the previous version of Emperor.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a78ccce87945`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.