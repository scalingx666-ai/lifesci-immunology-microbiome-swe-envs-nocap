# Issue

**Title:** Add ANIr coverage method

## Description

## Summary
- support new `anir` coverage method
- compute read identity in BAM processing
- expose ANIr via CLI and docs
- fix README example value
- test ANIr output

## Testing
- `cargo build` *(fails: failed to fetch from github)*
- `cargo test` *(fails: failed to fetch from github)*

------
https://chatgpt.com/codex/tasks/task_e_6876be75ced4832a80c3e221930d5e8d

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e062091b0263`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.