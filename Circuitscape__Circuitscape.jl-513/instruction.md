# Issue

**Title:** Reuse per-component batch buffers in the direct-solver pairwise loop

## Description

## Summary
- Default `cholmod_batch_size` drops from 1000 to 32. Multi-RHS triangular solves are memory-bandwidth bound and saturate well below that, while a 1000-column dense RHS and solution pair cost 16 GB at 1M cells.
- The RHS, solution and residual buffers are allocated once per component (sized `n × min(bs, npairs)`) and reused across batches. Only the ±1 entries are written and cleared; a final partial batch works on views.
- New `solve_linear_system!` writes into the preallocated buffer. CHOLMOD uses the in-place `ldiv!(X, F, B)`; other backends fall back to copying the allocating result.
- `refine_columns!` computes the whole batch's residuals with one sparse-times-dense `mul!` and only enters per-column refinement for columns that fail.
- Pardiso extension gains a matching in-place method (untested here, no MKL).
- Docs and the one test that hardcoded the batch size are updated.

## Measurements
Synthetic 500x500 raster, 40 focal points (780 pairs), CHOLMOD, cumulative current map on, Float64:

| | time | allocated | GC |
|---|---|---|---|
| master, batch 1000 | 11.5 s | 15.7 GB | 0.45 s |
| this branch, batch 32 | 10.5 s | 6.9 GB | 0.2 s |

Master with batch 32 still allocated 15.7 GB, so the buffer reuse and the smaller batch each contribute. The remaining allocation is per-pair current-map postprocessing, addressed separately.

## Test plan
- [x] `Pkg.test()`: unit, CG+AMG and CHOLMOD suites in double and single all pass. Accelerate and Pardiso suites skipped (packages not installed).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_016qia6G6xbgffF6ENXzAX8t

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1139e772a068`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.