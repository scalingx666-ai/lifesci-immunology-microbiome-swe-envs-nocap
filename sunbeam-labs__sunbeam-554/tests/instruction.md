# Issue

**Title:** Handle ruleorder for single-end reads

## Description

## Summary
- Use conditional rule order for adapter removal to prevent paired rule from executing on single-end data
- Apply same conditional ordering for trimmomatic rules

## Testing
- `snakefmt sunbeam/workflow/rules/qc.smk`
- `pytest tests/e2e/test_sunbeam_run.py::test_sunbeam_run_with_single_end_reads -q` *(fails: Conda environment creation blocked by proxy configuration)*

------
https://chatgpt.com/codex/tasks/task_e_6894b9423a4883238dafc618275b6889

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d5a97903a34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.