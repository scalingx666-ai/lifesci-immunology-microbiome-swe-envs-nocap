# Issue

**Title:** Make GTDB-Tk optional

## Description

## Summary
- move GTDB-Tk from the main Pixi environment to dev only
- handle missing GTDB-Tk in `singlem supplement`
- document optional GTDB-Tk requirement for supplement

## Testing
- `pytest test`
- `pixi lock` *(fails: tunnel error to conda channel)*
- `pixi run test` *(fails: tunnel error to conda channel)*

------
https://chatgpt.com/codex/tasks/task_e_68a418f55fc8832a8436507f873d5de2

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19b801c5d6fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.