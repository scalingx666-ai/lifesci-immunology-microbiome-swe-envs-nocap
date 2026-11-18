# Issue

**Title:** Simplify get_latents function

## Description

This function is only ever called with last_epoch=True, so just remove this argument. Also make it more type stable.

CC @Paupiera  - does this change make sense?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `655400932531`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.