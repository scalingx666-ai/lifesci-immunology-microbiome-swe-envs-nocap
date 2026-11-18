# Issue

**Title:** Remove ubuntu-20.04 from GitHub Actions workflows

## Description

This PR removes references to `ubuntu-20.04` from the GitHub Actions workflows as the runner will be deprecated on April 15, 2025. The workflows now use only `ubuntu-22.04`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6bd25823775`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.