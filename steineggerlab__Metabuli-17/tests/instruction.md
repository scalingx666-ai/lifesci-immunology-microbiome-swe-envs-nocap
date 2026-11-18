# Issue

**Title:** Fix issue#15: ignore reads shorter than 26 nt.

## Description

A query read should be at least 26 nt for the six-frame translation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dffa012c77e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.