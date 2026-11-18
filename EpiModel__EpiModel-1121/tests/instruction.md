# Issue

**Title:** Stop netsim when a module returns dat with an R attribute set on it

## Description

.

When magrittr is attached after EpiModel, `magrittr::set_attr()` (base `attr<-`) masks ours. A call like `set_attr(dat, "status", x)` then writes to `attr(dat, "status")` and returns `dat` with its class intact, so the existing `netsim_dat` return check passes and the model silently never updates.

`dat` only ever carries `names` and `class`, so `netsim_run_modules()` now checks `length(attributes(dat)) > 2L` after each module and stops with an error naming the module, the stray attribute, and the fix. The check costs about 0.2 µs per module per step, roughly 0.01% of a step in a 1,000-node tergmLite model.

The `posit_ids` form of the masked call already errors, with the less helpful `4 arguments passed to 'attr<-' which requires 3`, and is unchanged here.

Full local check with `NOT_CRAN=true` passes (4686 tests, none skipped).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a5cbc2afb2e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.