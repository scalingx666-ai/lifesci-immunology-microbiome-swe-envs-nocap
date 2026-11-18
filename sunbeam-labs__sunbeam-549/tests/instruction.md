# Issue

**Title:** Fix absolute paths in generated samples.csv

## Description

## Summary
- ensure `sunbeam init` resolves provided data directory
- write absolute file paths when generating the samples.csv file
- resolve filenames when loading from directories so paths remain absolute

## Testing
- `ruff check sunbeam/scripts/init.py sunbeam/project/sample_list.py`
- `pytest -q` *(fails: FileNotFoundError: [Errno 2] No such file or directory: 'sunbeam')*

------
https://chatgpt.com/codex/tasks/task_e_6887a6dba6f883238085d72790f72b0b

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce9a3ccceb07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.