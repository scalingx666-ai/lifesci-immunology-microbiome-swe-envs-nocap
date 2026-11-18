# Issue

**Title:** Adapt Parameters and CLI to mostly automatically stay in sync

## Description

Rather than hard-coding the available parameters in the CLI source, have it read the relevant set out of Parameters directly.

Fixes: #491

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a29aab979f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.