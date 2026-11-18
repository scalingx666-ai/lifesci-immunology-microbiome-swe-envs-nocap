# Issue

**Title:** Retry CG with tighter tolerances before failing; precision-aware residual gate

## Description

.

## The mismatch
`Krylov.cg` with a preconditioner stops on the **preconditioned** residual `√⟨r, M⁻¹r⟩`; the line after it accepts on the **true 2-norm** residual. When AMG is a poor fit for a component the two diverge — CG reports `solution good enough given atol and rtol` after 12 iterations while the true residual is `1.17e-4` — and the whole run dies on that one solve (2 of ~2,600 Omniscape windows in the report). No single constant fixes a check measured in a different norm than the stopping test; #406 loosening it to `1e-4` only moved the threshold.

## Fix
`solve_linear_system` tightens `atol` and `rtol` by 100× and retries, up to three attempts, logging each retry as a warning. Solves that pass first time are unaffected (Float64 suite: 719/719, zero retries). The final error carries the history (`after 3 attempts (last rtol = …, N iterations, <status>)`) so the next report doesn't need instrumenting.

## Precision-aware gate — and a finding
While wiring this up: **single precision has been broken on master**. The #462 cleanup hard-coded the gate to `1e-4` for both precisions, leaving `TOL_SINGLE`/`TOL_DOUBLE` in `consts.jl` unused. Float32 solves land at 1.0–1.8e-4 and every Float32 run aborts (`CG solver did not converge: relative residual 0.00018 exceeds tolerance 1e-4`). CI never noticed because `runtests.jl` only ever ran Float64 (#256 was closed without a guard).

Two things in Float32: Krylov's default `atol = √eps(T)` is ~3.4e-4 and is what actually stops CG there, so it must be tightened along with `rtol` on retry; and the default gate is now `1e-3` in single, `1e-4` in double (`TOL_DOUBLE` updated to the #406 value).

The gate is exposed as `residual_tolerance` in the INI (default `auto`; a number overrides both precisions) so Omniscape can set it. `multiple_solve` (advanced mode) gains `cfg` so it uses the same gate; its duplicated `@assert` on the residual is dropped. The CHOLMOD/Pardiso/Accelerate methods take the same `tol` keyword. Docs: new *Convergence Checks* section in `compute.md`, table row in `options.md`.

## Tests
`residual_tolerance` defaults per precision and round-trips through the INI dict; a solve on a model problem passes; `tol = 0.0` fails with the three-attempt message. Full Float64 suite passes (Unit 26/26, CG+AMG 719, CHOLMOD 719, Issue 341 46).

With this PR a Float32 pass gets 698/719 instead of aborting; the remaining Float32 failures are test-harness and Float32-accuracy issues unrelated to the gate and are handled in the single-precision CI PR, which will be based on this one.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9522ccaa056f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.