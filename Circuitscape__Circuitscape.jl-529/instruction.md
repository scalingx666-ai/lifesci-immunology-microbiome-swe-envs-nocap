# Issue

**Title:** advanced_kernel: no local copies for a whole-graph component

## Description

Part of reducing per-solve allocation for Omniscape (Circuitscape/Omniscape.jl#92), where GC time stays at ~5–6 s regardless of thread count and becomes over half the wall time at 16+ threads.

When one connected component spans the whole graph, which is the common case for an Omniscape moving window, `advanced_kernel` now uses `G` directly instead of `G[c, c]`. For rasters it also reuses the geometry instead of calling `restrict`, which rebuilt a nodemap identical to the original. Neither `multiple_solver` nor `accum_currents!` writes to the matrix, so sharing it is safe. Network geometries still go through `restrict`.

**Effect on a 201×201 window** (`compute_omniscape_current`, one direct ground, as Omniscape calls it): 118.2 → 109.8 MiB with cg+amg and 95.4 → 87.0 MiB with cholmod. Windows with nodata cells that still form one component save the same 7–8 MiB. Windows split into several components are unchanged.

## Test plan
- [x] Full `Pkg.test()` passes. The existing advanced and Omniscape tests cover both the whole-graph and the multi-component paths.
- [x] Local harness: 16 window configurations (cg+amg/cholmod; plain, nodata, multi-component, 4-neighbour; direct and finite grounds). Every current map is bitwise identical to master.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `382cc4676892`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.