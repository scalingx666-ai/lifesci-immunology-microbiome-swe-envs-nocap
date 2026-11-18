# Issue

**Title:** Fix issue 1016 - cumulative edgelists at t=1

## Description

.

## Summary

The cumulative edgelist saved by `netsim` (`mod$cumulative.edgelist$sim1` when `cumulative.edgelist = TRUE`) was dropping a few edges relative to the networkDynamic object that `netsim` also saves. In Steve's MRE (attached to #1016), `as.data.frame(get_network(mod, sim = 1))` returned 305 rows while `mod$cumulative.edgelist$sim1` returned 302; the 3 missing spells all had `onset = 0, terminus = 1`. The same bug caused persistent edges to be recorded with `start = 2` instead of `start = 1` (a silent off-by-one), and dropped edges with `onset = 0/terminus = 2` and `onset = 1/terminus = 2` in larger simulations.

## Root cause

`update_cumulative_edgelist()` is called only from `resim_nets()`, which first runs at `at = 2`. Initialization (`sim_nets_t1()` at `at = 1`) never touched the cumulative tracker, so:

1. At `at = 2` the tracker was empty, and persistent edges got `start = 2` (off-by-one).
2. Edges active at `at = 1` but not at `at = 2` (networkDynamic terminus is exclusive, so spells like `onset = 0/terminus = 2` or `onset = 1/terminus = 2` were already gone from `get.dyads.active(net, at = 2)`) were in neither the tracker nor the current edgelist, and silently dropped.
3. Edges active only during the initial ERGM to TERGM step (`onset = 0, terminus = 1`) were dropped for the same reason, and are invisible to `get.dyads.active(net, at = 1)` as well.

## Fix

New internal helper `seed_cumulative_edgelist_t1()` in `R/edgelists.R`, called once at the end of `sim_nets_t1()`:

- Seeds `el_cuml_cur` with edges active at `at = 1` (both tergmLite and non-tergmLite), each with `start = 1`. This resolves the off-by-one and the `onset = 0/terminus = 2` / `onset = 1/terminus = 2` cases. They are now in the tracker at `at = 1` and get properly transitioned to history with `stop = 1` when `update_cumulative_edgelist()` runs at `at = 2`.
- For non-tergmLite (and when `truncate.el.cuml != 0`): additionally seeds `el_cuml_hist` with dyads active at `at = 0` but not at `at = 1`, with `start = 1, stop = 1`. Uses point-in-time `get.dyads.active(nw, at = 0)` / `get.dyads.active(nw, at = 1)` queries (not `as.data.frame(nw)`), to avoid double-counting future spells when `resimulate.network = FALSE` pre-simulates the full trajectory at init.

`update_cumulative_edgelist()` itself is unchanged.

### Design notes

- **`start = 1, stop = 1`** for initial duration-1 edges rather than `stop = 0`: `make_restart_point()` filters `el_cuml_hist` to `stop >= 1`, so `stop = 0` would silently drop these rows on restart.
- **Seed placed inside `sim_nets_t1()`, not `initialize.net()`**: `sim_nets_t1` is only called on the fresh-start branch (`control$start == 1`). On restart (`control$start > 1`), `el_cuml_cur` / `el_cuml_hist` arrive pre-populated from the prior run, so the seed must not fire.
- **tergmLite limitation (documented in NEWS)**: `networkLite` keeps only the current `el` and `lasttoggle`, so initial-step dissolutions are unrecoverable there. The fix seeds what it can (persistent edges at `start = 1`) and leaves the limitation documented.
- **The head/tail semantic reversal** Steve flagged as a side note is preserved; fixing it would be a breaking change for downstream consumers and belongs in a separate issue.

## Files changed

- `R/edgelists.R`: new `seed_cumulative_edgelist_t1()`.
- `R/net.mod.simnet.R`: call the seed at end of `sim_nets_t1()`.
- `tests/testthat/test-cumulative_edgelist.R`: 3 new tests (row-count parity vs networkDynamic, `truncate.el.cuml = 0` hist-seed skip, tergmLite `start = 1`).
- `NEWS.md`: bug-fix entry under 2.6.1 BUG FIXES.

## Test plan

- [x] Added regression test reproducing Steve's MRE in miniature (asserts `nrow(cumulative.edgelist) == nrow(as.data.frame(networkDynamic))` and that initial duration-1 edges appear with `start = 1, stop = 1`).
- [x] Added test for `truncate.el.cuml = 0` to confirm the default active-only behavior is preserved.
- [x] Added tergmLite test confirming the off-by-one fix applies there too.
- [x] Ran full test-cumulative_edgelist.R file locally: 18 pass, 0 fail.
- [x] Reproduced Steve's exact MRE after the fix: cumulative edgelist now has 305 rows (was 302), matching the networkDynamic count; the 3 previously-missing dyads appear with `start = 1, stop = 1`.
- [x] CI: `R CMD check --as-cran` across platforms.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8106d1f98c70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.