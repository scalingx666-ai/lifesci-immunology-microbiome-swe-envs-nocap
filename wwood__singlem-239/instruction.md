# Issue

**Title:** Move setup script to admin and add AGENTS instructions

## Description

## Summary
- Move setup script into `admin/` and adjust path resolution for repository root
- Add `AGENTS.md` instructing contributors to source the setup script before running commands or tests

## Testing
- `source admin/setup.sh && orfm -h | head -n 20`
- `source admin/setup.sh && pytest test/test_orf_length_checker.py -k small --maxfail=1`

------
https://chatgpt.com/codex/tasks/task_e_689d28728258832a8220d07640762fd2

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad79996f373b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.