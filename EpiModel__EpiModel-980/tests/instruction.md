# Issue

**Title:** Remove extension model support from ICMs

## Description

## Summary

- Formally removes custom/extension module support from the ICM model class
- ICMs now exclusively support the built-in SI, SIR, and SIS disease types
- Users needing custom epidemic models are directed to the network model class (`control.net()`)

## Motivation

ICMs were always intended as pedagogical "gateway" models between DCMs and network models — not as a platform for custom epidemic modeling. The extension support that existed (passing custom `.FUN` modules via `...` in `control.icm()`) was partial and undocumented: it allowed bolting extra modules onto a base type but never supported fully custom models the way `control.net(type = NULL)` does. No vignettes, tutorials, or training materials ever referenced ICM extensions, and only a single test exercised the feature.

Removing this capability makes the API clearer: ICMs are simple built-in models for learning, network models are the extension platform for research.

## Changes

- **`control.icm()`**: Removed `.FUN` formal parameters, `skip.check`, and `...`. Signature is now just `type`, `nsteps`, `nsims`, `verbose`, `verbose.int`.
- **`crosscheck.icm()`**: Simplified to always assign built-in modules. Removed user module detection and `skip.check` gating.
- **`icm()` simulation loop**: Removed the user modules execution block.
- **`print.control.icm()`**: Removed "Base Modules" / "Extension Modules" display.
- **Documentation**: Updated roxygen for `control.icm`, `param.icm`, and `modules.icm` to remove extension language and direct users to network models.
- **Tests**: Replaced the "ICM new modules" test with a test verifying that custom `.FUN` args produce an error.
- **NEWS.md**: Added breaking change entry.

## Test plan

- [x] Verify `R CMD check` passes (CI)
- [x] Verify `control.icm(type = "SI", nsteps = 10)` works as before
- [x] Verify passing custom `.FUN` args to `control.icm()` produces a clear error
- [x] Verify all built-in ICM tests pass (SI, SIR, SIS, 1-group, 2-group)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8223bdbb9dc9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.