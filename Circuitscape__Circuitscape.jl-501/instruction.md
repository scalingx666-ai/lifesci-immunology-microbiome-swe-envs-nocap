# Issue

**Title:** Compute node currents in one sweep without sparse temporaries

## Description

Part of the unreleased 6.0.

## The problem

`get_node_currents(G, voltages, finitegrounds)` in `src/out.jl` called `_get_node_currents_posneg` twice (pos/neg). Each call built a sparse branch-current matrix with `sparse(I, J, b, N, N)`, formed `B - B'`, ran `dropnonzeros!`/`dropzeros!`, optionally added `spdiagm(0 => finiteground_currents)`, and finally took `sum(dims=1)`. That is roughly six sparse temporaries of size `nnz(G)` per focal pair, allocated by every worker thread concurrently. With current maps on, GC pressure from this postprocessing dominated the solve.

## The change

The per-node result is `max(total inflow, total outflow)`. For every off-diagonal entry `(row, col)` of the symmetric Laplacian, `b = |G[row,col]| * (v[row] - v[col])` is the current arriving at `col` from `row`: positive is inflow at `col`, negative is outflow. Because each undirected edge is stored in both columns, a single sweep over the CSC structure (`nzrange` per column, skipping the diagonal) collects both totals for a node from its own column, in the same row-sorted order the old `B - B'` column sum used. Finite grounds contribute `finitegrounds[i] * v[i]` with the same sign split as before (negative is inflow, positive is outflow), and the `finitegrounds[1] != -9999` sentinel still means "no finite grounds".

One subtlety: the old code zeroed branch currents smaller than `1e-8` relative to `maximum(b)` of the *signed* branch-current vector, separately for the pos and neg directions. To reproduce those results exactly, a first allocation-free pass over `nzval`/`voltages` recovers both reference maxima (upper-triangle entries give the pos reference, lower-triangle entries the neg one), and the accumulation pass applies the same threshold. The two accumulators are scalars per column, so only the output vector is allocated.

`_get_branch_currents` is unchanged and still used for the network branch-current output. `_create_current_maps` now returns `nothing` instead of `spzeros(0,0)` for the raster placeholder, so the raster postprocess path builds no sparse matrix at all. It still scatters node currents into one fresh full-grid `zeros` per pair, as before, with no other copies.

Removed: `_get_node_currents_posneg`, `dropnonzeros!` (no remaining callers).

## Measurements

1000x1000 grid Laplacian (8-neighbour, `construct_graph(ones(n,n), ..., true, false)` then `laplacian!`), n = 1,000,000 nodes, nnz = 7,988,004, random `randn` voltage vector, no finite grounds. Julia 1.12.7, Apple Silicon. Timings were taken while other test suites ran on the same machine, so they are noisy; allocation counts are exact.

| implementation | `@allocated` | best-of-3 time |
|---|---|---|
| old (`B - B'`, sparse) | 967.2 MB | 0.407 s |
| new (single CSC sweep) | 8.01 MB (the output vector) | 0.038 s |
| ratio | 121x less | ~10.6x faster |

Maximum relative difference between old and new on this problem: `2.0e-16`.

## Tests

- New `@testset "get_node_currents matches sparse reference"` in `test/internal.jl` keeps the old implementation verbatim as a local reference and compares against it on: the `model_problem` grid Laplacian (7x7, 8-neighbour), a random sparse symmetric Laplacian with isolated nodes, each with and without finite grounds, in both `Float64` (rtol 1e-12) and `Float32` (rtol 1e-6), plus the `[-9999.]` Float64 sentinel on a Float32 problem as `core.jl` passes it. Two hand-checked 3-node path cases are included.
- Gold-file suites (current maps, cumulative and max maps) pass unchanged.

Full suite, `JULIA_NUM_THREADS=4 julia --project=. -e 'using Pkg; Pkg.test()'` (ArchGDAL not installed, so GeoTIFF fixtures skipped; 685 instead of 719 per suite):

```
Unit tests                 |  538    538
CG+AMG, parallel, Float64  |  685    685
CG+AMG, parallel, Float32  |  685    685
CHOLMOD, parallel, Float64 |  685    685
CHOLMOD, parallel, Float32 |  685    685
Issue 341: included pairs  |   46     46
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca524b6d8f49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.