# Issue

**Title:** Add dependency checks for x-mapper mapping program

## Description

## Summary
- add a `MappingProgram::check_dependencies` helper so each mapper, including x-mapper, validates its external tools when selected
- update the CLI parser to invoke the shared dependency check and adjust the x-mapper command test expectation
- resolve recent clippy findings uncovered by the hook

## Testing
- cargo fmt
- cargo clippy -- -D warnings
- cargo test

------
[Codex Task](https://chatgpt.com/codex/tasks/task_e_6913ae10e08c832aa140d2f16ba26f87)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a641b2a1bc0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.