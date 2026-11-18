# Issue

**Title:** Fix parallel test failures, remove SimpleWeightedGraphs/PrecompileTools

## Description

## Summary
- Fix `compute_with` to always set `parallelize` explicitly — it only set `true` but never `false`, so the INI file's `parallelize=True` was always used. Tests requesting sequential execution were silently running in parallel, causing intermittent CI failures.
- Replace `SimpleWeightedGraphs` with `SimpleGraph` from Graphs.jl — only graph structure is needed for `connected_components`, not weights
- Remove `PrecompileTools` and the precompile workload
- Restore CI test matrix: all 3 platforms for regular tests, Ubuntu for Pardiso
- Increase CI thread count from 2 to 4

## Test plan
- [x] CI passes on all platforms with `JULIA_NUM_THREADS=4`

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b6dca19b6118`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.