# Issue

**Title:** Add an AMGX GPU solver as a package extension

## Description

Adds `solver = amgx`, which solves on an NVIDIA GPU through [AMGX.jl](https://github.com/JuliaGPU/AMGX.jl), as the package extension `CircuitscapeAMGXExt`. Load it with `using AMGX`. Also bumps the version to 6.2.0.

## Design

- **Algorithm.** CG preconditioned by one V-cycle of AMGX's classical AMG (PMIS coarsening, D2 interpolation, symmetric multicolor Gauss–Seidel). On the BigTests grids it takes 7–8 iterations. AMGX's aggregation AMG took 40–110 and was 5–8× slower per solve.
- **Pairwise.** Uses the batched path already shared by CHOLMOD, Pardiso and Accelerate: one GPU hierarchy per connected component, `cholmod_batch_size` right-hand sides per batch, and every column checked against `residual_tolerance` on the host by `refine_columns!`.
- **Advanced, one-to-all and all-to-one.** Build and free a handle for each solve. AMGX calls go through one lock because one-to-all solves on several threads; graph construction and current accumulation still run in parallel.
- **New `release!(handle)` hook.** A no-op by default. The pairwise driver and `multiple_solve` call it so GPU objects are destroyed deterministically. AMGX is initialized lazily and finalized at exit.
- **Upstream workaround.** Works around NVIDIA/AMGX#80: a solve with `zero_inital_guess = true` on a reused vector returns the vector's old contents plus the new solution. The extension zeroes the vector itself, so it works with released AMGX.jl and doesn't depend on the fix in JuliaGPU/AMGX.jl#53.
- **Timing.** The batched path now records its linear solves under `"solve linear system"`, matching the CG+AMG path.
- **Indices.** `amgx` uses the same 32-bit index threshold as `cg+amg`. AMGX needs fewer than 2^31 stored entries per component, about 230M cells with eight neighbors.
- **Compat.** Requires AMGX.jl 0.2.2, the version everything below was tested with. AMGX.jl ships prebuilt binaries for Linux.

Making config keys and values case-insensitive was split out to #534.

## Tests

The full suite passes on an H100: CG+AMG, CHOLMOD and AMGX, each in Float64 and Float32 (685 checks each), plus the unit and included-pairs tests. Pardiso and Accelerate were skipped because they aren't available on this machine. AMGX tests run only when AMGX.jl is loadable and CUDA is functional, so **CI, which has no GPU, does not exercise the extension.**

## Benchmarks: BigTests, pairwise, resistances only, double precision

GPU is one H100 NVL. CPU is a 2×32-core EPYC 9354 with 64 Julia threads, on a shared machine whose other jobs run at nice 19. Times in seconds.

**One pair, end to end:**

| Cells | CHOLMOD | CG+AMG (Julia, CPU) | AMGX (GPU) | AMGX vs CG+AMG | AMGX vs CHOLMOD |
|---|---|---|---|---|---|
| 1M | 2.3 | 3.8 | 1.0 | 3.9× | 2.4× |
| 6M | 16.0 | 29.2 | 5.2 | 5.6× | 3.1× |
| 12M | 45.8 | 61.7 | 10.7 | 5.8× | 4.3× |
| 24M | 85.0 | 130.9 | 20.8 | 6.3× | 4.1× |
| 48M | 162.1 | 266.0 | 42.2 | 6.3× | 3.8× |
| 96M | not run | 516.0 | 83.2 | 6.2× | — |

**Setup and one solve:**

| Cells | CHOLMOD factor / solve | CG+AMG setup / solve | AMGX setup / solve |
|---|---|---|---|
| 1M | 1.6 / 0.12 | 0.93 / 2.43 | 0.16 / 0.04 |
| 6M | 11.2 / 0.81 | 5.2 / 20.3 | 0.91 / 0.19 |
| 12M | 26.1 / 1.63 | 10.4 / 43.9 | 1.8 / 0.42 |
| 24M | 54.0 / 3.44 | 20.8 / 94.8 | 3.4 / 0.89 |
| 48M | 108.8 / 6.87 | 40.9 / 194.3 | 6.6 / 1.75 |
| 96M | — | 77.7 / 376.3 | 12.6 / 3.46 |

**20 focal points (19 solves), end to end:**

| Cells | CHOLMOD | CG+AMG (CPU) | AMGX (GPU) |
|---|---|---|---|
| 1M | 3.0 | 4.6 | 1.6 |
| 6M | 20.1 | 40.1 | 8.2 |
| 12M | 45.2 | 82.2 | 17.4 |
| 24M | 93.9 | 171.9 | 34.3 |
| 48M | 188.4 | 337.2 | 70.4 |
| 96M | not run | not run | 137.9 |

- **AMGX setup is about 6× faster than CG+AMG's and 10–16× faster than CHOLMOD's factorization.** Each AMGX solve is 50–110× faster than CG+AMG and 3–4× faster than a CHOLMOD triangular solve.
- **End to end, AMGX is 4–6× faster than CG+AMG and 2–4× faster than CHOLMOD.** The rest of the time is on the CPU and the same for every solver: loading the map, building the graph and building the per-component node map. At 96M that is about 60 of AMGX's 83 seconds, so it's the next bottleneck to work on.
- **Memory.** 96M cells fit on one H100, with peak host RSS of 65 GB. CHOLMOD peaked at 68 GB at 48M; it and the 96M CPU 20-point run were skipped for time and memory on the shared machine.
- **Accuracy.** AMGX resistances agree with CG+AMG within 1.1e-4 relative at every size.
- **Ill-conditioned BigTests (10^8 resistance contrast).** AMGX matches CHOLMOD within 1.2e-5 and is 3–4× faster: 4.9 s vs 16.5 s at 1M cells, 6.1 s vs 24.6 s at 6M. CG+AMG on the CPU did not finish the 1M case within 25 minutes. Both CHOLMOD and AMGX reject the 10^15 case, as expected.

An Omniscape comparison modeled on Circuitscape/Omniscape.jl#92 (radius-668 windows, about 1.4M cells each) is running and will be posted as a comment.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c26cb15edca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.