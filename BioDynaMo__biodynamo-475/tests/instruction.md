# Issue

**Title:** Repair CI

## Description

Restore the repository's supported CI build configurations.

- The architecture job selected the earlier distribution image. Select the updated distribution image.
- CMake cache filtering parsed unquoted values and tested a variable name for the NOTFOUND marker. Retain only defined cache values by quoting names and expanded values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c619d133616`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.