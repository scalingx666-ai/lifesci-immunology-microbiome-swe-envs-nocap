# Issue

**Title:** Terminate GHA when branch updates

## Description

Add concurrency check to GHA. If you commit to the same branch quickly after each other, this will stop previously launched runs and avoid waiting for previous runs to finish or manually terminating them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ee9d9db343c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.