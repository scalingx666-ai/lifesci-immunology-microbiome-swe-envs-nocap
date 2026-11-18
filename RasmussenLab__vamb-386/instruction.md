# Issue

**Title:** Log the file taxonomy is loaded from

## Description

This is generally useful, and in particular helps with a current CI issue where the wrong file is seemingly loaded in CI

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0c1a2afebe1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.