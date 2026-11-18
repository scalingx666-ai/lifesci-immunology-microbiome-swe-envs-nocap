# Issue

**Title:** add missing template

## Description

a bit embarrassing, but I forgot to add the actual html template for the new admin page in PR #3417 ... and no test did catch this mistake :-/

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd2d9b79b80b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.