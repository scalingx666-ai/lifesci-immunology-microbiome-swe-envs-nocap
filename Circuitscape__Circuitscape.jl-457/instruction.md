# Issue

**Title:** Improve thread safety of cumulative map accumulation and I/O

## Description

## Summary
- Replace global `CUM_LOCK` with a per-instance `lock` field in the `Cumulative` struct, so concurrent `compute()` calls no longer contend on a shared lock
- Remove `mycsid()` and the single-element `Vector` wrappers on `Cumulative` fields (vestige of the old `Distributed.jl` design)
- Remove `IO_LOCK` from `write_currents`/`write_voltages` since they only use `writedlm`, not GDAL
- Narrow `IO_LOCK` in `write_raster` to only wrap the `ArchGDAL.create` call — data preparation (`permutedims`, etc.) now runs outside the lock

## Test plan
- [x] Full test suite passes locally (Unit tests: 17, CG+AMG: 719, CHOLMOD: 719, Issue 341: 24)
- [x] CI passes on all platforms

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d30d0fe546ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.