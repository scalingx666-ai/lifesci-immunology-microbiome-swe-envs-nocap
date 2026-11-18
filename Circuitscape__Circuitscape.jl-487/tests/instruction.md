# Issue

**Title:** Unify the AMG and direct-solver pairwise drivers

## Description

`core.jl` had two ~200-line copies of the pairwise driver — `solve(::AMGSolver)` and `solve(::Union{CholmodSolver,PardisoSolver,AccelerateSolver})` — differing only in how the linear systems are solved. Everything else (component loop, pair enumeration, exclusion, shortcut, resistance bookkeeping, `Output`/`postprocess`, logging) was duplicated, so every change had to land twice: #472 gated the log lines in one copy and #473 in the other; the residual gate is duplicated the same way.

## Shape
One `solve(prob, solver::Solver, …)`:
- `pair_jobs` enumerates `PairJob`s per component, grouped by source node, skipping pairs whose every focal-index combination is excluded (the shortcut path asks for the first source only).
- `handle_pair(job, voltages)` stores the resistance for every non-excluded index combination and runs `postprocess`. Each `(c_i, c_j)` is owned by exactly one job, so concurrent writes never overlap.
- Only two functions are solver-specific: `prepare!` (AMG: regularize in place + build the preconditioner; direct: factorize) and `solve_pairs!` (AMG: one pair at a time, parallel over source nodes, per-task preconditioner workspace and timer; direct: batches of `cholmod_batch_size` right-hand sides, parallel postprocess per batch).

`core.jl` 744 → 585 lines; `CholmodNode` and the results-vector `smash_repeats!` are gone.

## Behaviour
Results are identical for every solver. One intentional difference: the direct path used to issue one RHS column per focal-*index* combination, so a pair of focal regions produced duplicate columns; it now, like the AMG path always did, solves once per node pair and stores the result for each combination. Fewer solves, same numbers.

## Tests
Full suite locally on **CG+AMG 719/719, CHOLMOD 719/719, Apple Accelerate 719/719**, Unit 17/17, Issue 341 46/46. Pardiso not available locally (no MKL on arm64); the Pardiso method of `solve_linear_system` is untouched and CI covers it on Windows/Ubuntu.

## Merge order
Touches the same region of `core.jl` as #485 (scoped timer) and #486 (#470 retry). Whichever lands second needs a rebase — the conflicts are mechanical (`CSTIMER` → `CSTIMER[]`, and passing `tol` into the two `solve_linear_system` calls). Happy to do it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3fb63980a34b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.