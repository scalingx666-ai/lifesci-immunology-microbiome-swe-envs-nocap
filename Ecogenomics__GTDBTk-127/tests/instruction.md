# Issue

**Title:** check for empty seq and empty file

## Description

There was a bug - when all the archaeal sequences had too little alignment the process tried to go through

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ffdab5047e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.