# Issue

**Title:** Fix outdated python2 scripts

## Description

## Summary
- upgrade Python 2 helper scripts to Python 3
- remove deprecated extras scripts

## Testing
- `pytest -k test_placeholder -q` *(fails: ModuleNotFoundError)*

------
https://chatgpt.com/codex/tasks/task_e_68747fe38058832a8e774913bca386a5

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6c21141c8aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.