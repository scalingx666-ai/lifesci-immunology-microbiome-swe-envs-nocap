# Issue

**Title:** Make the job timer a ScopedValue instead of a global

## Description

`CSTIMER` was one global `TimerOutput` that `_run` reset at the start of every `compute()`, so two concurrent jobs in one process — Omniscape solving windows in parallel, or two `compute` calls from separate tasks — reset and merged into each other's timings.

Each `_run` now binds a fresh `TimerOutput` via `Base.ScopedValues.with` for its dynamic extent; `Threads.@spawn`ed tasks inherit it, so the per-thread `merge!` calls keep working. All `@timeit CSTIMER` sites become `@timeit CSTIMER[]`; no other code changes. `ScopedValues` is in `Base` from Julia 1.11, which is the declared lower bound.

Verified the `log_level = DEBUG` timing table still prints. Full suite passes locally.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a98db13073a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.