# Issue

**Title:** Sembin sample counting bug

## Description

When there was a short read and a long read (or multiple long reads), the pre model would be used, which silently crashed semibin.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e123cdebe8a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.