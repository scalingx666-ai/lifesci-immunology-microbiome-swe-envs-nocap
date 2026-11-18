# Issue

**Title:** Address doc clarity for accessor functions

## Description

## Summary

Clarifies the intended scope of the `get_*` / `set_*` / `add_*` / `append_*` accessor functions and of `update_params()`, motivated by #1024.

The functions are designed to operate on the live `netsim_dat` object that `netsim()` constructs internally and passes through user-supplied module functions at every time step. They are not a general-purpose tool for editing user-facing `param.net` / `init.net` / `control.net` inputs before a run, nor for editing the object returned by `netsim()`. Applying them outside that context (as in the example in #1024) appears to succeed because everything is list-like, but it produces an object that isn't a valid simulation input. The behavior is intentional and consistent across the whole accessor family, but the docs never said so explicitly.

This PR is documentation-only.

## Changes

- `R/net.fn.accessor.R`
  - One-sentence pointer added to `@description` flagging the intended scope.
  - New `@section Intended Usage:` covering: the expected calling context (inside module functions during a `netsim()` run); what *not* to call these on (input or output objects); and the right alternatives for the common outside-simulation needs (`update_params()`, direct list assignment, fresh constructor calls) and for scheduled mid-simulation changes (`.param.updater.list` / `.control.updater.list`, scenario API).
  - `@seealso` cross-referencing `update_params()`, the input constructors, and `netsim()`.
- `R/net.inputs.R`
  - `update_params()` `@details` extended to contrast outside-simulation use (`update_params`) with inside-module use (`set_param`); notes the lack of `update_controls()` / `update_inits()` siblings and points at `.param.updater.list` / `.control.updater.list` for mid-simulation changes.
  - `@seealso` added.
- `man/net-accessor.Rd` and `man/update_params.Rd` regenerated via `roxygen2::roxygenise()`.

## Test plan

- [x] CI: `R CMD check --as-cran` passes (doc-only change, but confirms cross-references and Rd render).
- [x] Spot-check rendered help: `?\`net-accessor\`` shows the new Intended Usage section; `?update_params` shows the new details paragraph and Seealso block.

 once merged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a159733ec65`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.