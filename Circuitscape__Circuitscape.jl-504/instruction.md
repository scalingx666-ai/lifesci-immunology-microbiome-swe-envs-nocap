# Issue

**Title:** Cut peak allocation in construct_graph

## Description

Part of the unreleased 6.0.

## The problem

`construct_graph` (`src/raster/pairwise.jl`) is what turns the raster into a sparse adjacency matrix, and it runs at load time, exactly when the largest grids are most likely to run out of memory. It was doing three memory-hungry things:

1. `push!`-ing every edge into three growing vectors `I`, `J`, `V`, so the buffers were repeatedly reallocated and copied as they grew;
2. building `a = sparse(I, J, V, m, m)` from those (the one-directional half of the graph);
3. `a = a + a'`, which materialises the transpose and then a second full matrix for the sum.

Peak allocation was roughly 3x the size of the final matrix, and for a 2000x2000 eight-neighbour grid it allocated ~2.5 GiB to produce a 0.5 GB matrix.

## The change

- A cheap first pass over `nodemap` (`count_graph_edges`) counts the edges, so `I`, `J`, `V` are allocated once at exactly `2 * nedges`.
- The second pass emits **both orientations** of every edge into those buffers, so the COO -> CSC conversion yields the symmetric matrix directly and `a + a'` is gone.
- The conversion uses `SparseArrays.sparse!` (the documented driver behind `sparse`) with `J` and `V` handed back as the storage for the result's `rowval` / `nzval`, so no fresh CSC matrix is allocated at all. `colptr` gets its own `(m + 1)`-vector: recycling `I` for it would shrink `I`'s length but keep its `2 * nedges` buffer alive (this was visible as a larger `Base.summarysize` on the result until fixed).
- `sparse!` sums duplicate `(i, j)` pairs exactly as `a + a'` did when a polygon maps adjacent cells to the same node (duplicates and self-loops), so the polygon path is unchanged too. For plain rasters there are no duplicates across the two orientations because each undirected edge is visited once, from the cell to its right/lower/diagonal neighbours.
- A `DimensionMismatch` guard on `size(gmap) == size(nodemap)` makes the `@inbounds` loops sound.

The four averaging functions (`res_avg`, `cond_avg`, `weird_avg`, `weirder_avg`), the four-neighbour flag semantics and `construct_node_map` are untouched. The result is the same `SparseMatrixCSC` (same `colptr`, `rowval`, `nzval`), so `laplacian!` and everything downstream sees an identical matrix.

## Measurements

2000x2000 all-ones grid, eight-neighbour (`four_neighbors = false`, `avg_res = false`), `nnz = 31,976,004`. Julia 1.12.7, Apple Silicon. Other agents were running test suites concurrently on this machine, so timings are noisy; allocation figures are exact.

| | old (`push!` + `a + a'`) | new | change |
|---|---|---|---|
| `@allocated` | 2,659,465,744 B (2536.3 MiB) | 1,375,142,448 B (1311.4 MiB) | -48 % |
| best-of-3 time (under load) | 0.305 s | 0.218 s | -29 % |
| `Base.summarysize(result)` | 543,616,232 B | 543,616,232 B | identical |
| `A_old == A_new` and `colptr`/`rowval`/`nzval` equal | | `true` | |

(A second, earlier run under different load gave 0.318 s vs 0.148 s; the allocation numbers were identical.)

## Tests

`test/internal.jl` gains a testset that keeps the **old** `construct_graph` (verbatim `push!` + `sparse` + `a + a'`) as a local reference `construct_graph_ref` and asserts, for every combination of `avg_res` and `four_neighbors`, that the new function returns a `SparseMatrixCSC` with identical `colptr`, `rowval`, `nzval`, `nnz`, `==`, and `issymmetric`, on:

- a 5x5 all-ones grid and a 5x5 grid with non-uniform resistances;
- a 6x7 grid with NODATA holes (nodemap zeros) in the interior, on edges and in corners;
- 1xN and Nx1 grids (both uniform and non-uniform);
- a polygon-style nodemap where adjacent cells share a node (duplicate pairs and self-loops that `sparse!` must sum exactly as `a + a'` did);
- the existing 3x3 fixture.

Full suite after rebasing onto current `master` (`JULIA_NUM_THREADS=4 julia --project=. -e 'using Pkg; Pkg.test()'`), ArchGDAL absent so GeoTIFF fixtures are skipped as expected:

```
Unit tests                 |  793    793  27.5s
CG+AMG, parallel, Float64  |  685    685   3.3s
CG+AMG, parallel, Float32  |  685    685  14.2s
CHOLMOD, parallel, Float64 |  685    685   2.9s
CHOLMOD, parallel, Float32 |  685    685   3.4s
Issue 341: included pairs  |   46     46   0.2s
     Testing Circuitscape tests passed
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62187e8845e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.