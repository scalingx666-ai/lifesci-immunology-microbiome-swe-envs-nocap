# Issue

**Title:** checkm2: Update to 1.1.0.

## Description

Unclear about how to handle DB update, but it seems to work with the old DB anyway.

Actually might need to check the download instructions to make sure they work before merging this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e123cdebe8a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.