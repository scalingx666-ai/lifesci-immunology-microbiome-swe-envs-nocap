# Issue

**Title:** Continue CG from its solution when the residual check fails

## Description

`solve_linear_system` accepts a CG solution only when its true relative residual is below `residual_tolerance` (#470). When the check failed, the retry restarted CG from zero with a 100× tighter `rtol`, so the whole solve was repeated. Retries now **warm-start from the returned solution** and ask for a further 100-fold reduction. `atol` still tightens on each retry, and there are still at most 3 attempts before an error.

## Why it matters

For a grounded problem, the retry is the normal case rather than the exception. That includes every Omniscape moving window, which grounds the center node. On a window-sized grid (868k nodes, centre grounded, sources spread out):

| | CG iterations | true relative residual |
|---|---|---|
| first attempt, rtol 1e-6 | 28 | 8.2e-4 (fails 1e-4) |
| current retry: restart from 0, rtol 1e-8 | +34 (62 total) | 7.8e-6 |
| this PR: continue from solution, rtol 1e-2 | +7 (35 total) | 6.7e-6 |

Solves that pass on the first attempt are unchanged.

## Measured

The Omniscape workload from Circuitscape/Omniscape.jl#92: radius-668 windows (about 1.4M cells each) on a 2000×2000 BigTests landscape, 361 windows, CPU `cg+amg`, 64 threads, two interleaved rounds on a 2×32-core EPYC 9354:

- master: 209.7 s and 208.1 s
- this PR: 168.8 s and 169.5 s, **19% faster**

The output current map is identical (total current 1.78043e+08 in every run).

## Other changes

- The retry is now logged with `@debug` instead of `@warn`. It is routine for grounded problems and otherwise emits one warning per Omniscape window.
- The convergence docs in `compute.md` and `options.md` describe the new behavior.

## Tests

The full suite passes: unit tests, plus CG+AMG and CHOLMOD in Float64 and Float32. The #470 test still checks that an unreachable tolerance fails "after 3 attempts".

Related: #537 (32-bit indices for Omniscape windows), Circuitscape/Omniscape.jl dynamic window scheduling, JuliaLinearAlgebra/AlgebraicMultigrid.jl V-cycle allocation. Together they make that 64-thread Omniscape run 1.73× faster.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `676139797e8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.