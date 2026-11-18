# Issue

**Title:** Change readlink to realpath to fix relative links.

## Description

with the change from readlink to realpath.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b014034d5c0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.