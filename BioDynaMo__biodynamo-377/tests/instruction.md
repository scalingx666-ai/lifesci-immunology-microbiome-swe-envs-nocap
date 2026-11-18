# Issue

**Title:** Updated CI workflows for macOS, Ubuntu and CentOS

## Description

This should fix #373. Now the CI ensures that the repository URL is dynamically constructed based on the environment

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2240cecee529`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.