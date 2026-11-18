# Issue

**Title:** Add check for existing directory

## Description

The command `biodynamo new <project>` had a bug, i.e. running it twice with the same `<project>` would just delete the existing folder and crash. Now, it checks if the project exists and, if so, asks the user to overwrite or not.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23e3409520df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.