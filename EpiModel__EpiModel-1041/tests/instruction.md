# Issue

**Title:** Remove stale ICM custom-module documentation

## Description

## Summary

.

After #980, ICMs are restricted to the built-in SI, SIR, and SIS disease types, but three help pages still described support for "original models" built from "new process modules":

- `?icm` (`R/icm.R`) — details paragraph about base + original models
- `?param.icm` (`R/icm.inputs.R`) — "Models may use the base types... or new process modules"
- `?init.icm` (`R/icm.inputs.R`) — "handles initial conditions for both base models and original models using new modules"

This PR replaces that language with direct statements that ICMs support SI/SIR/SIS only, and points custom-model users to `netsim()` with `control.net(type = NULL, ...)` (for `?icm`), `param.net()` (for `?param.icm`), and `init.net()` (for `?init.icm`). The wording mirrors the cleanup already done in `?control.icm` and `?modules.icm` in #980.

## Other changes

- Dropped the now-redundant "for base models" qualifier in the `@return` outputs bullet of `?icm` and the second details paragraph of `?param.icm`, since there are no other model types.
- Added a one-line NEWS entry under v2.6.2 → OTHER.
- Re-ran `roxygen2::roxygenise()` to regenerate `man/icm.Rd`, `man/param.icm.Rd`, `man/init.icm.Rd`. The run also picked up `man/param.net.Rd`, which was out of date relative to the current `param.net()` source (the regenerated text matches what `R/net.inputs.R` already says about `data.frame.params` / `data.frame.parameters`).

## Test plan

- [ ] CI green (no code changes, doc-only)
- [ ] Spot-check rendered Rd: `?icm`, `?param.icm`, `?init.icm` no longer reference "original models" or "new process modules"
- [ ] Verify pointers in the new text resolve: `[netsim()]`, `[param.net()]`, `[init.net()]`, `[control.net()]`

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `296bf53f14c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.