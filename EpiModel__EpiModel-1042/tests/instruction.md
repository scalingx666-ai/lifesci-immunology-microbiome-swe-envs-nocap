# Issue

**Title:** Validate per-step module return values in netsim

## Description

## Summary

.

`netsim_run_modules()` now checks `inherits(new_dat, "netsim_dat")` after each user-supplied module call (per Adrien's note on the issue). When a custom module forgets `return(dat)`, the simulation stops immediately with a clear error naming the offending module, instead of failing on the next module with the misleading `argument "dat" is missing`.

Before:
```
Error in get_control(dat, ...) : argument "dat" is missing
```

After:
```
A ERROR occured in module 'my_extension.FUN' at step 2
Module 'my_extension.FUN' did not return a `netsim_dat` object (got NULL).
The most common cause is a missing `return(dat)` at the end of the module function.
```

## Implementation note

The check assigns the module's output to a temporary `new_dat` first and only overwrites `dat` once validated. If the validation throws, the enclosing `dat` is still the last known-good `netsim_dat`, which the existing `withCallingHandlers` error handler relies on. `netsim_error_logger()` calls `get_control(dat, ".traceback.on.error")`, so leaving `dat` intact lets the error path keep working. A short comment in the loop explains the indirection.

Scope is intentionally limited to the per-step module loop (the location the issue identifies). `initialize.FUN` validation could be added separately if the same class of bug shows up there.

## Test plan

- [x] New tests in `test-newmodules.R` cover the NULL-return case (forgotten `return(dat)`) and the wrong-class case (`unclass(dat)`); both now produce the expected error.
- [x] Existing `test-newmodules.R` passes (81 / 81 with `NOT_CRAN=true`).
- [x] Full **EpiModel-Gallery** runs cleanly against the patched package, confirming no false positives on real custom-module patterns:
  - cost-effectiveness, hiv, multinets, observed-network-data, seir-aon-vaccination, seir-exposed-state, seirs-leaky-vaccination, si-vital-dynamics, sis-competing-strains, sis-test-and-treat, social-diffusion, syphilis (12 / 12 OK).
- [ ] CI green.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb489377380e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.