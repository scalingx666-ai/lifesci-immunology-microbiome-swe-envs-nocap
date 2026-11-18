# Issue

**Title:** laplacian!: build the Laplacian without temporaries

## Description

Part of reducing per-solve allocation for Omniscape (Circuitscape/Omniscape.jl#92).

`laplacian!` used to allocate the row sums, a diagonal sparse matrix and `G + S`. Now:
- when every column already stores its diagonal entry, the Laplacian is written into `G` with no allocation;
- otherwise it is built in one pass that inserts the diagonal, and `G` is left as is.

Zeros are dropped as `G + S` dropped them, so the result is bitwise identical.

**Effect:** a 201×201 window goes from 8.3 to 5.8 MiB in `laplacian!` (118.2 → 115.8 MiB for the whole `compute_omniscape_current` call). The raster `construct_graph` doesn't store diagonals, so for now it takes the one-pass path. Once #523 lands, a follow-up could reserve the diagonal slots in `construct_graph`'s `sparse!` call. That would make every raster Laplacian in place and save the remaining ~6 MiB per window. I left it out here to avoid conflicting with #523.

## Test plan
- [x] Added assertions to the existing `construct_graph` block: the inserted-diagonal result matches `Diagonal(colsums) - A` with no entry for an isolated node, and with a stored diagonal `laplacian!` returns `G` itself with the same structure.
- [x] Full `Pkg.test()` passes.
- [x] Local fuzz (not committed): 80k random symmetric matrices (Float64/Float32, Int64/Int32; all, some or no diagonals stored; explicit zeros) give `colptr`/`rowval`/`nzval` identical to the old implementation.
- [x] Window harness (16 configurations): current maps bitwise identical to master.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `382cc4676892`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.