# Issue

**Title:** Default extensions path to home directory

## Description

## Summary
- default SUNBEAM_EXTENSIONS to `~/.sunbeam/extensions`
- create extension directory if missing
- document new default extension location

## Testing
- `pytest -q` *(fails: conda not installed, `sunbeam` CLI missing)*

------
https://chatgpt.com/codex/tasks/task_e_68acf4344b708323a56a48bdd540d0a8

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6005a8de8995`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.