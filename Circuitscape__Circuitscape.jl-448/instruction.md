# Issue

**Title:** Replace IterativeSolvers.jl with Krylov.jl

## Description

## Summary

Replace IterativeSolvers.jl with Krylov.jl for the CG solver. Krylov.jl is actively maintained, generally faster, and supports GPU out of the box. IterativeSolvers.jl has not had meaningful updates in years.

## Changes

- `using IterativeSolvers` → `using Krylov`
- `cg(G, curr, Pl=M, reltol=T(1e-6), maxiter=100_000)` → `Krylov.cg(G, curr, M=M, ldiv=true, rtol=T(1e-6), itmax=100_000)`
- `ldiv=true` is needed because AlgebraicMultigrid's preconditioner implements `ldiv!`, not `mul!`

## Test plan

- [ ] All tests pass on all platforms

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7925edb899e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.