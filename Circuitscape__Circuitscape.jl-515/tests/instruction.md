# Issue

**Title:** Default to Int32 sparse indices when the graph fits

## Description

## Summary
- The `use_64bit_indexing` option already existed and the index type `V` already flowed generically through the raster and network data, graph construction, `GraphProblem`, CHOLMOD, AlgebraicMultigrid and Krylov. In practice everything ran on Int64 because the default was `true`.
- `index_type(cfg, nnodes, nnz)` picks Int32 when the node count is under a solver-dependent limit and the nnz bound fits in 31 bits, else Int64. The limits are 100M nodes for `cg+amg`, whose memory is a small multiple of the Laplacian, and 8M nodes for the direct solvers, whose Cholesky factor must fit 32-bit indices too (fill crosses 2^31 around 15 to 20M cells with AMD). `use_64bit_indexing` now defaults to `false` and still forces Int64 when set.
- If CHOLMOD nevertheless rejects a 32-bit factorization as too large, the error now names the component and says to set `use_64bit_indexing = true` or switch to `cg+amg`.
- Fixed silent promotion back to Int64: `matrix + sparse(10eps*I, n, n)` in the Accelerate and Pardiso paths and `spdiagm` in advanced mode always produced Int-indexed matrices. A shared `regularize(matrix)` builds the shift in the matrix's index type. CHOLMOD uses the `shift` argument from #512 and needs no copy. The Accelerate extension converts to Int64 transiently because `AAFactorization` only accepts Int64.
- `compute_omniscape_current` stays on Int64 as its docstring promises.
- Unit tests cover both limits on both sides; the verification suite now runs on Int32 by default and one existing case still covers Int64 explicitly.

## Measurements
1000x1000 raster, 1M nodes, 8-connected, Float64, 1 thread:

| | Int64 | Int32 |
|---|---|---|
| Laplacian (nnz 9.0M) | 145 MB | 107 MB |
| CHOLMOD peak | 943 MB | 827 MB |
| AMG hierarchy | 508 MB | 382 MB |
| maxrss after graph build | 1350 MB | 1097 MB |

Full `compute` runs, 65 focal points, identical checksums:

| solver | Int64 | Int32 |
|---|---|---|
| cholmod | 5491 MB, 14.7 s | 5141 MB, 14.3 s |
| cg+amg | 3143 MB, 73.2 s | 2406 MB, 71.5 s |

## Test plan
- [x] `Pkg.test()`: unit, CG+AMG and CHOLMOD suites in double and single, issue 341 all pass on Int32 against the reference outputs.
- [x] Verification suite with the Accelerate solver on Int32 in a scratch environment passes.
- [ ] Pardiso extension not executed locally (no MKL); CI covers it.
- [ ] The CHOLMOD too-large path needs a factor over 2^31 entries and is verified by reading only.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c08979c4ae3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.