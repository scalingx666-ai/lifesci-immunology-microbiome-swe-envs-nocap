# Issue

**Title:** Deduplicate write_grid in out.jl

## Description

Part of the unreleased 6.0.

## The problem
`src/out.jl` had two near-identical `write_grid` methods. The variant taking a `cellmap` re-inlined the log-transform and null-to-nodata logic that `process_grid!` already implements, and both copies carried their own filename-suffix selection (`curmap` / `cum_curmap` / `max_curmap` / `voltmap`). Two copies of the same logic invite drift.

## The change
Collapse the two methods into a single `write_grid(cmap, name, cfg, hbmeta, cellmap = nothing; voltage, cum, max, log_transform, set_null_to_nodata)`. When a `cellmap` is given it delegates to `process_grid!`; the suffix logic now exists exactly once. Every existing call site (`out.jl`, `raster/advanced.jl`) works unchanged. Purely mechanical, no behaviour change.

## Tests
Full suite with `JULIA_NUM_THREADS=4`, green (GeoTIFF fixtures skipped locally without ArchGDAL, as expected):

```
Unit tests                 |  488    488
CG+AMG, parallel, Float64  |  685    685
CG+AMG, parallel, Float32  |  685    685
CHOLMOD, parallel, Float64 |  685    685
CHOLMOD, parallel, Float32 |  685    685
Issue 341: included pairs  |   46     46
```

The gold-file comparisons of current, voltage and cumulative maps are the check that output is byte-identical.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ad337c2f4f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.