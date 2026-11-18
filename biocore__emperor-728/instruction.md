# Issue

**Title:** Fix a problem where invisible or transparent objects would be intersected

## Description

This PR explicitly removes objects that are not visible when raycasting.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `027aa16f1dcf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.