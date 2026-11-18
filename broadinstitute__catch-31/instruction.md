# Issue

**Title:** Simplify determination of package version

## Description

See 7550a1f for most substantive changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0cb3e87048b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.