# Issue

**Title:** Catch unpaired or duplicate read files during init

## Description

## Summary
- raise explicit errors when sample reads are missing R1/R2 mates or when duplicate read files exist
- expand unit tests for SampleList to cover missing pairs and extra files

## Testing
- `black .`
- `pytest tests/unit/`

------
https://chatgpt.com/codex/tasks/task_e_68b0d10372f88323a8a088c01ff2eaf1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3662829e6e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.