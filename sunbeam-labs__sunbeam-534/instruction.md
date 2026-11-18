# Issue

**Title:** Fix integration test command

## Description

## Summary
- fix the integration test workflow's `sunbeam run` invocation

## Testing
- `pytest -q` *(fails: conda not found)*

------
https://chatgpt.com/codex/tasks/task_e_684b6b8fc12c83238e0a7bfc1892b553

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31a47b7aeade`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.