# Issue

**Title:** split out networkLite as a separate package

## Description

Companion PR to statnet/networkDynamic#16 and EpiModel/networkLite#4.

Updates EpiModel to work with a separate networkLite package.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5930e8b1f82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.