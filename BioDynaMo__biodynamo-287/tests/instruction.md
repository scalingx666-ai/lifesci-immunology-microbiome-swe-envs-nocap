# Issue

**Title:** Fix macos openmp

## Description

Since OpenMP was updated to version 15.0.3 on MacOS, CMake was unable to locate it. This PR fixes the issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6e2c80b010c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.