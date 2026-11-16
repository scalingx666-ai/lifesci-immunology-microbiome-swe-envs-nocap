# Issue

**Title:** Add GitHub Actions workflow for R-CMD-check with CmdStan integration

## Description

This commit introduces a new GitHub Actions workflow to automate R package checks using CmdStan. The workflow supports multiple operating systems and R versions, ensuring comprehensive testing. It includes steps for setting up the environment, installing CmdStan, and checking R package dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6f1aa11b665`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.