# Issue

**Title:** Use config-defined log file

## Description

## Summary
- define a `log_fp` under `all` in the default Sunbeam config
- use the configured `log_fp` when setting up the pipeline logger
- load configuration in `sunbeam run` to drive logging
- test configuration helpers recognize and resolve `log_fp`

## Testing
- `pytest tests/unit -q`
- `pytest -q` *(fails: ModuleNotFoundError: No module named 'snakemake.cli')*

------
https://chatgpt.com/codex/tasks/task_e_689b99203bec83238d471d4d848a2066

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aabaa83ef28a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.