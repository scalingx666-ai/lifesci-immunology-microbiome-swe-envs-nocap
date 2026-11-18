# Issue

**Title:** Rename getQCMetrics and addQCMetrics to getQC and addQC

## Description

Shorter names, as suggested in #859. The old names have not been in a release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a15be3fd2c5b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.