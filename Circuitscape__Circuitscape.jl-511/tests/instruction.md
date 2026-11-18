# Issue

**Title:** Make compute_omniscape_current safe to call concurrently

## Description

`compute_omniscape_current` is Omniscape's entry point and is called from many tasks at once. It ran outside any `with(CSTIMER => ...)` scope, so every concurrent call timed into the single default `TimerOutput` held by the scoped value. `TimerOutput` is not thread-safe, and with 4 worker threads Omniscape's test suite failed with `UndefRefError` inside `advanced_problem`. The same race existed in 5.17.1's global `CSTIMER`.

Each call now runs under its own timer, matching what `compute` does per run. The parallel sections in `core.jl` already use per-task timers merged after `fetch`, so nothing else needed to change.

Adds a test in `test/internal.jl` that solves from 64 tasks concurrently and checks every result against the serial one. Full suite passes on Julia 1.12.7 and 1.13.0-rc4 with 4 threads.

Companion: Circuitscape/Omniscape.jl#171.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01C6f7jh7ZZ9mwJDx8baPLeR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aae1b996dc0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.