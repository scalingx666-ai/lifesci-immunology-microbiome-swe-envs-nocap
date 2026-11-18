# Issue

**Title:** fix environment_script for private plugins

## Description

I found that patch 54.sql for the test database uses an old conda activate mechanism for travis. We might want to fix this to the latest github action method of choice?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e673bd90b9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.