# Issue

**Title:** Add debug logs to project config objects

## Description

## Summary
- improve debug logging in project config classes

## Testing
- `black sunbeam/project/*.py`
- `pytest tests/unit -q`
- `pytest -q` *(fails: FileNotFoundError: [Errno 2] No such file or directory: 'sunbeam' due to missing conda/sunbeam executable)*

------
https://chatgpt.com/codex/tasks/task_e_685ef9135b848323815d08314d16b7b7

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37dbb10c94be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.