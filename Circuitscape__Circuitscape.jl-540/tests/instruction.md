# Issue

**Title:** Reuse one Krylov workspace and residual buffer across CG attempts

## Description

`solve_linear_system` (the `cg+amg` solve) allocated a fresh Krylov workspace for every attempt and two temporaries for every residual check:

- first attempt: `Krylov.cg` builds a workspace of 5 vectors of the system's size
- each warm-started retry (#536): another workspace of 6
- each residual check, `norm(G*v .- curr)`: 2 more

It now builds one `Krylov.CgWorkspace` and one residual buffer per solve and reuses them across attempts (`Krylov.cg!`, with the warm start passed the workspace's own solution, which Krylov copies before overwriting). A solve that needs one retry, as every Omniscape window does, now allocates 7 vectors instead of 15; one that passes first time, 6 instead of 7.

**Results are bit-identical** to master (relative difference 0.0 on an 800×800 grid Laplacian, Float64 and Float32, with and without a retry).

**Effect on Omniscape:** on 9 real radius-668 windows (single thread, Circuitscape, AlgebraicMultigrid and Omniscape at master), allocation drops from 1.870 to 1.833 GB per window, about 2%, with the same total current. Most of what remains is AMG setup and graph construction, not the CG solve; the CG + AMG path itself is type stable and allocates essentially nothing per iteration.

The `CgWorkspace(A, b)` constructor and the warm-start form of `cg!` exist from Krylov 0.10.0, so the compat bound is unchanged.

Full test suite passes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eace7c389f1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.