# Issue

**Title:** fix: removed the max-retries parameter as it no longer exists

## Description

- remove max-retries from rosella commands during refinement
- Was causing crashes in

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `177fcd095965`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.