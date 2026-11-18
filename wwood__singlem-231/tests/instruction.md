# Issue

**Title:** Fix NotImplementedException usage

## Description

## Summary
- update `graftm_result` to raise `NotImplementedError`

## Testing
- `pytest -q` *(fails: ModuleNotFoundError: No module named 'bird_tool_utils')*

------
https://chatgpt.com/codex/tasks/task_e_6875c32f1778832a8c4e9a8a2782fbe5

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c70b55467932`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.