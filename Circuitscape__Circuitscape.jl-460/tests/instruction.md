# Issue

**Title:** Fix parallel solver stability and improve code clarity

## Description

## Summary
- Set `BLAS.set_num_threads(1)` at module init — Circuitscape's workload is sparse and does not benefit from multi-threaded BLAS, but multi-threaded BLAS can produce corrupted results when multiple Julia tasks run concurrent Krylov CG solves (BLAS routines like `dot`, `norm`, `axpy` on dense vectors)
- Rename AMG and CHOLMOD solver closures and variables for clarity, replacing single-letter names (`f`, `g`, `i`, `j`, `I`, `J`, `v`, `r`, `d`, `X`) with descriptive names (`solve_pairs_for_point`, `build_cholmod_batch`, `postprocess_pair`, `src_node`, `dst_node`, `voltages`, `resistance`, `pair_numbers`, etc.)
- Solve each `(src_node, dst_node)` pair once in the AMG path instead of redundantly for every index combination when focal points are duplicated
- Downgrade per-solve logging inside spawned tasks from `@info` to `@debug` to avoid I/O contention in the parallel hot path
- Replace `sum(abs2)` test checks with element-wise comparison that reports specific mismatched entries and failure counts (via `@debug`)

## Test plan
- [x] Full test suite passes locally with 4 threads (Unit: 17, CG+AMG: 719, CHOLMOD: 719, Issue 341: 24)
- [x] CI passes on all platforms



🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6a2c50711da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.