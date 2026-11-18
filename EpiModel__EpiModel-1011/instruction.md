# Issue

**Title:** Clean up duplicated quantile/mean logic in plot_netsim_epi() and plot.icm()

## Description

, , .

## Summary

Cleans up duplicated quantile/mean-line logic in both `plot_netsim_epi()` (`R/plot.netsim.R`) and `plot.icm()` (`R/plot.icm.R`), and fixes a latent `ylim` bug in the netsim path. The two functions share `draw_qnts()` / `draw_means()` helpers in `R/plot.R`, so `CLAUDE.md` requires changes to be coordinated across them — this PR does both.

### Deduplication in `plot_netsim_epi()` (#997)

1. **Single `disp.qnts` setup.** The quantile enable/validate logic previously appeared in both the ylim-calc phase and the drawing phase (the latter with a `## NOTE: Why is this repeated from above?` comment). It now runs once, before either phase.
2. **Single `mean.lwd` / `mean.lty` expansion.** The `rep()` expansion that padded these vectors to length `lcomp` previously ran twice; the second call was a no-op. Now runs once under a single `if (mean.line)` guard.
3. **Consistent `draw_qnts()` / `draw_means()` signatures.** Both phases now pass all positional args explicitly (`"epi"`, `0|1`, `"max"`, `offset`) instead of relying on the drawing-phase defaults matching the ylim-phase explicit args.

Also removes trailing `qnts.pal[1:y.l]` / `mean.pal[seq_len(y.n)]` subsetting in the drawing phase — the helpers only index palettes at `[j]` for `j in seq_len(lcomp)` and the legend call below takes `length(legend)` entries from `col`, so the subsetting was cosmetic.

### ylim bug fix in `plot_netsim_epi()` (#1009)

The `ylim` auto-calc branch used `qnts == TRUE` in its guard, which only matched `qnts = 1` / `qnts = TRUE`. For the default `qnts = 0.5` with `mean.line = FALSE`, `ylim` was never expanded to fit the quantile polygon even though it was drawn. Now uses `disp.qnts` (available from the deduplication consolidation above), so `ylim` tracks whatever is actually plotted. The sentinel `qnt.*` / `mean.*` initializers (`±1E10`) ensure the `min`/`max` formula still works correctly in the previously-exercised `mean.line=TRUE` / `nsims=1` case.

### Matching cleanup in `plot.icm()` (#1010)

Applies the same three-part consolidation to `plot.icm()` so it stays structurally symmetric with `plot_netsim_epi()`.

**Secondary effect**: `plot.icm()` previously guarded only on `nsims > 1`, so passing `qnts = FALSE` with `nsims > 1` would still call `draw_qnts()` with `qnts = FALSE`, producing a degenerate `c(0.5, 0.5)` quantile band (effectively invisible, but not cleanly skipped). The consolidated `disp.qnts` guard now skips the polygon call entirely for `qnts = FALSE`, aligning the implementation with the function's own documentation: *"To toggle off the polygons where they are plotted by default, specify `qnts=FALSE`"*. No user-visible change for the default `qnts = 0.5` path; users relying on `qnts = FALSE` now get the documented behavior.

## Behavior preservation

For `plot_netsim_epi()`, verified `disp.qnts` construction across `(qnts, nsims)` combinations — `FALSE/5`, `0/5`, `0.5/5`, `0.5/1`, `TRUE/5`, `1/5` — all match the original control flow. The `qnts == FALSE` form (rather than `isFALSE(qnts)`) is kept deliberately to preserve R's coercion behavior at `qnts = 0`.

For `plot.icm()`, default-path behavior (`qnts = 0.5`, `nsims > 1`, `mean.line = TRUE`) is unchanged; only the `qnts = FALSE` edge case is affected (now skipped as documented).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd61e07c2ebc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.