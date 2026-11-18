# Issue

**Title:** Creates new GitHub Action for standalone testing

## Description

New workflow "Empress Standalone CI" that creates a non-QIIME2 environment and runs tests that do not require and QIIME2 dependencies. `test_cli` updated to not use the Artifact API.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26aa6ac1ec70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.