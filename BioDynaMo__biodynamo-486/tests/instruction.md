# Issue

**Title:** Add the Xcode 26.1 ROOT package for earlier Xcode 26 releases

## Description

Select ROOT 6.36.06 for Xcode 26.0 through 26.5 and register its Apple Silicon checksum. Keep the separate ROOT 6.40.04 package for Xcode 26.6 and newer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c531f0038b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.