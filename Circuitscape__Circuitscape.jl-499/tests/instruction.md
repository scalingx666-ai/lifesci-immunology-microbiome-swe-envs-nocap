# Issue

**Title:** Fix wrong focal nodes dropped by read_point_map

## Description

Part of the unreleased 6.0.

## The problem

`read_point_map` (`src/io.jl`) removes negative focal-node values by collecting their indices with `findall` and then calling `deleteat!` once per index inside a loop. After the first deletion every later index in the list is off by one, so with two or more negative entries the wrong focal nodes are removed: a negative value survives and a valid node silently disappears. If the last negative entry is near the end of the vector, the shifted index runs past the end and throws `BoundsError`. On master, a point file containing the values `1, -1, 2, -2, 3` returns focal nodes `[-2, 1, 2]` instead of `[1, 2, 3]`.

## The change

Delete all flagged indices with a single `deleteat!(x, ind)` call per vector, which Base handles correctly for a sorted index collection. Both the ASCII-grid and text-list (`FILE_TYPE_TXTLIST`) branches share this code path, so both are fixed.

The other `deleteat!` call sites in `src/` (`prune_points!`, `prune_strengths`, `multiple_solver`, the included-pairs reader) already collect indices and call `deleteat!` once, so no change is needed there.

## Tests

New `test/read_point_map.jl` (included in the "Unit tests" testset) builds a 5x5 point grid and equivalent text lists containing `1, -1, 2, -2, 3`, plus a text list with a trailing negative, and asserts `read_point_map` returns exactly `v = [1, 2, 3]` at rows `[2, 4, 5]` and columns `[1, 3, 5]`. Before the fix: 6 failures (`[-2, 1, 2] == [1, 2, 3]`, etc.) and 1 `BoundsError`; after: 9/9 pass.

Full suite with `JULIA_NUM_THREADS=4` (ArchGDAL absent, GeoTIFF fixtures skipped):

```
Unit tests                 |  497    497
CG+AMG, parallel, Float64  |  685    685
CG+AMG, parallel, Float32  |  685    685
CHOLMOD, parallel, Float64 |  685    685
CHOLMOD, parallel, Float32 |  685    685
Issue 341: included pairs  |   46     46
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ad337c2f4f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.