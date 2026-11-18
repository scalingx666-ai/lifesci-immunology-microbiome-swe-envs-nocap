# Issue

**Title:** Minor improvement to summariser.py logging.

## Description

This was printing very large lists and causing buffer overflows when trying to run as a subprocess...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce9a3eb10137`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.