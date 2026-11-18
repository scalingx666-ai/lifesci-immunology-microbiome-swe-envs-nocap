# Issue

**Title:** Add preprocess report parsers and summary aggregation

## Description

## Summary
- implement parsing helpers for adapter, quality, complexity, and decontam reports and generate the combined TSV output
- support multiple report files per sample and guard the snakemake entrypoint
- add unit tests covering the new parsers and integration

## Testing
- pytest tests/unit

------
https://chatgpt.com/codex/tasks/task_e_68e548d0d8d4832380e217c3ddf5ec8f

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d7dd6ce4881`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.