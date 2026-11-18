# Issue

**Title:** Type stability fixes from a JET pass

## Description

## Summary
A JET `@report_opt` pass found the numerical hot path type stable; the instabilities were in driver and setup code. This fixes the ones with a measurable cost or a large report count.

- **`CSConfig(cfg; kwargs...)`** built the 46-field copy through a splatted generator, so the whole call was dynamic. It is now a `@generated` copy with compile-time field names. This is called once per moving window by `compute_omniscape_current`. An unknown keyword now throws `ArgumentError` instead of `MethodError`.
- **`solve`**: `num_pairs`, `pair_numbers` and `resistances` were captured by closures and reassigned in the shortcut branch, boxing them as `Any` and making the per-pair handler dispatch dynamic. Each is now assigned once. `Core.Box` count 33 to 0. The shortcut branch no longer logs the un-reduced pair count before the reduced one.
- **`cum::Cumulative{T,V}`** in `GraphProblem` and `Output` (was `Cumulative{T}`, not concrete). `initialize_cum_maps` takes the index type instead of hard-coding `Int`, since raster runs can now use `Int32`.
- **`write_asc`**: header scalars hoisted into `_asc_origin` so the `open do` closure no longer boxes them. Output identical.
- **`run_onetoall`**: the two-argument `f` closure renamed `_pt`, the per-point body moved to a top-level `solve_onetoall_point` function barrier, and `create_new_polymap`'s `map` closures replaced with loops that no longer box `newpoly`.

## JET reports before and after
| Target | Before | After |
|---|---|---|
| `CSConfig(cfg; solver=)` | 2 | 0 |
| `solve` | 36 | 1 |
| `accumulate_currents!` | 4 | 0 |
| `write_asc` | 12 | 0 |
| `run_onetoall` | 83 | 9 (all inside `advanced_kernel`, pre-existing) |

`CSConfig` copy: 10.9 µs and 17.6 KB per call before, 0.7 µs and 0 bytes after.

## Test plan
- [x] `Pkg.test()` with 4 threads: unit, CG+AMG and CHOLMOD suites in double and single, issue 341 all pass against the reference outputs.

Spotted but not changed: in `create_new_polymap`, the `length(nz) == 1` branch reads `overlap`, which is only defined in the `else` branch, so that path would raise `UndefVarError` if hit.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26521a966c3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.