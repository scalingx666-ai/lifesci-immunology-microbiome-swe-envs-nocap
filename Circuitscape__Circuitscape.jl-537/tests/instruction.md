# Issue

**Title:** Use 32-bit node indices in compute_omniscape_current

## Description

`compute_omniscape_current`, Omniscape's entry point for every moving-window solve, hard-coded `V = Int64`. INI runs, by contrast, pick 32-bit indices through `index_type` whenever the problem fits, and a moving window always fits. This PR chooses the index type with `index_type(cfg, ncells, raster_nnz_bound(ncells))`, as `load_data` does, so `use_64bit_indexing = true` still forces 64-bit. The config is now parsed before the raster data is built so `index_type` can see it, and the docstring no longer says indices are always `Int64`.

## Why it matters

Profiling Omniscape (Circuitscape/Omniscape.jl#92) shows the solves are memory-bandwidth bound and GC heavy at high thread counts. At 64 threads:
- IPC falls from 2.37 (1 thread) to 1.58.
- Pipeline slots stalled on memory rise from 19% to 37%.
- GC pauses take about 28% of the run.

32-bit indices shrink the Laplacian, its AMG hierarchy and every index vector, so each concurrent solve moves and allocates less memory.

## Measured

Same workload as #536: radius-668 windows (about 1.4M cells each), 361 windows on a 2000×2000 BigTests landscape, CPU `cg+amg`, 64 threads, two rounds each.

| | wall (s) | allocated |
|---|---|---|
| master | 209.7, 208.1 | 1166 GB |
| #536 | 168.8, 169.5 | 1098 GB |
| #536 + this PR | 133.9, 131.7 | 875 GB |

Measured on top of #536, this PR is **21% faster** on its own and allocates 20% less. The total current is identical in every run (1.78043e+08).

## Tests

The full suite passes, including the existing `compute_omniscape_current` tests: the serial result against concurrent calls from many tasks.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bd8916f05c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.