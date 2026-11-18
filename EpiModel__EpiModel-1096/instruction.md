# Issue

**Title:** Make old set_epi() and record_*() calls error

## Description

Follow-up to EpiModel/EpiModel#1007, into `dev`.

With the new signatures, an old positional call like `set_epi(dat, "x", at, value)` still runs but records the time step as the value, and `record_raw_object(dat, at, label, obj)` stores the wrong label and object. No error, just wrong output. This makes those calls stop instead.

- `set_epi()`, `record_attr_history()` and `record_raw_object()` take `...` before `at`, so `at` (and `posit_ids`, `unique_ids`) has to be named. Anything that lands in `...` stops with an error giving the old and new signatures and the fix, and `attribute =` / `values =` get a note that they are now `item` / `value`. Inside `netsim()` the error names the module.
- They also check that `item` or `label` is a single string and that `at` is a single number, and say so clearly when `at` is `NULL` and `dat` has no current time step.
- Fixes the four old-form calls left in the tree: `test-netclique.R` (its `reused` tracker was all `NA`, so the test passed by accident), `test-merge.R`, the `record_raw_object()` example, and the vignette.
- New tests for the default `at`, the input checks, the old-signature errors, and that the module `at` matches the step `set_epi()` records at, including after a restart.
- NEWS: one breaking entry for the three signature changes, with a migration example. Code that has to run on both 2.6.x and 2.7.0 passes `at` and the ID arguments by name and the rest by position, e.g. `set_epi(dat, "x", value, at = at)` or `record_attr_history(dat, "x", value, posit_ids = ids, at = at)` (checked on CRAN 2.6.2 and this branch). The same goes into the "Removed and Renamed Arguments" section of CLAUDE.md and AGENTS.md.
- Attributes vignette: fixes the `get_epi()` argument order in the aging example and the raw records example (the queue needs `$as_list()`, so it returned `NULL`), and updates the `get_attr_at()` and `get_attr_history()` output, which no longer matched. The output shown is from this branch merged with #1097, which restores the first-recorded order of `get_attr_history()`.
- The `record_*()` docs pointed to "Time-Varying Parameters" in the parameters vignette; they now point to the attributes vignette.

The formatting of the tracking entries in NEWS is fixed in #1097, which rewrites those entries anyway. Doing it here too would make the two PRs conflict. They merge cleanly with each other.

Checked locally (R 4.6.1, macOS): `lintr::lint_package()` finds nothing, and `R CMD build` (with vignettes) plus `NOT_CRAN=true R CMD check --no-manual` is OK with no notes, 4067 tests passing. The same check on this branch merged with #1097 is also OK (4333 tests).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `911099aa4ddd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.