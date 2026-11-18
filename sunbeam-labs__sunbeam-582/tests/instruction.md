# Issue

**Title:** Ensure sunbeam run -h displays subcommand help

## Description

## Summary
- prevent the top-level CLI parser from consuming subcommand help flags
- allow `sunbeam run -h` to print the run-specific help text

## Testing
- pytest tests/unit/

------
https://chatgpt.com/codex/tasks/task_e_68ee706f24248323b6fd1942864d1e02

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81d074375a95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.