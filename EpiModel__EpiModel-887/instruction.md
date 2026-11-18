# Issue

**Title:** add `save.diss.stats` to the checked controls

## Description

this control governs the saving of the dissolution statistics. It's no set to FALSE by default if not set within the `control` list. This prevent issues with project that implement their own `control_` function

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2bd6918e33d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.