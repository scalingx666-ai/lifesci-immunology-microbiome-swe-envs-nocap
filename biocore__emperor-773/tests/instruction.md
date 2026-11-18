# Issue

**Title:** Fixes an issue with parallel plots and augments the select API

## Description

- When a user visualized biplots, they wouldn't be able to swtich to parallel plot mode without some markers being left behind. This needed a bit of refactoring of some underlying methods #747.

- Expand the selection API to return the view object (this is for better integration with Empress) - #771 .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c1f61652913`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.