# Issue

**Title:** Deduplicate paired taxonomy queries

## Description

## Summary
- combine paired-end window sequences so each aligned sequence is queried once per package
- map query hits back to both forward and reverse read names for each sample

## Testing
- pixi run -e dev pytest test

------
[Codex Task](https://chatgpt.com/codex/tasks/task_e_693776b3e574832aad873f4ea4f2b06a)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad9eaf977dd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.