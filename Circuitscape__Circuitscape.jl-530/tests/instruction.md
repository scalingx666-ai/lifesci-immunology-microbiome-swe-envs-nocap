# Issue

**Title:** multiple_solver: copy the matrix at most once

## Description

Part of reducing per-solve allocation for Omniscape (Circuitscape/Omniscape.jl#92).

`multiple_solver` copied the component matrix twice when there were finite grounds (`a + diagonal`, then `asolve[r, r]`). It also made one full copy when there were none, since `r` was then every node. Now:
- with no direct grounds, `a` is solved as is, plus one copy if there are finite grounds;
- with direct grounds, `a[r, r]` makes the one copy and the finite grounds are added to its diagonal in place (new `add_diagonal!`, which falls back to `A + sparse(r, r, d)` when a diagonal entry is missing). Zeros are dropped as sparse `+` dropped them.

`a` is never written to.

**Effect on a 201×201 window:** about 6 MiB less when there are finite grounds (127.1 → 121.3 MiB with cg+amg). Omniscape's usual window has a single direct ground and no finite grounds, so it still needs the one copy and is unchanged by this PR.

## Test plan
- [x] Extended the existing multiple_solver check in "index type" with a direct + finite ground case against a dense reference solve, and asserted `a` is unchanged (Int32 and Int64).
- [x] Full `Pkg.test()` passes.
- [x] Local fuzz (not committed): `add_diagonal!` against `A + sparse(r, r, d)` on 40k random matrices (stored zeros, missing diagonals, negative entries) gives identical `colptr`/`rowval`/`nzval`. `multiple_solver` against the old implementation on 1200 random raster Laplacians (AMG and CHOLMOD, Int32/Int64, direct/finite/mixed grounds) gives bitwise identical voltages, identical `sources` mutation, and `a` untouched.
- [x] Window harness (16 configurations): current maps bitwise identical to master.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b522cf790fd0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.