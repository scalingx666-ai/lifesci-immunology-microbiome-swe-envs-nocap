# Issue

**Title:** Replace custom logging with CSLogger AbstractLogger

## Description

## Summary
- Implement `CSLogger <: AbstractLogger` that handles timestamps, message suppression, file logging, and UI callback forwarding in `handle_message`
- Remove `csinfo`/`cswarn` helper functions — all call sites now use standard `@info`/`@warn`
- Remove `suppress_messages` parameter threading through function signatures — the logger handles suppression based on `cfg.suppress_messages` set once at initialization via `update_logging!`
- Remove unused `suppress_info` parameter from `construct_cholesky_factor` and `multiple_solve`
- Eliminates the `Dict{String,Any}` logging state that caused type instability on every log call

## Test plan
- [x] Full test suite passes locally (Unit tests: 17, CG+AMG: 719, CHOLMOD: 719, Issue 341: 24)
- [ ] CI passes on all platforms

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18f943246ae3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.