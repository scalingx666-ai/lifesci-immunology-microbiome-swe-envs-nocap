# Issue

**Title:** Fix unit tests for v2.3.2 push

## Description

When I run `testthat::test_package()` on EpiModel, this triggers this Warning:

```r
── Warning (Line 27): environment handling in non-nested EDA ───────────────────
Argument(s) ‘from.new’ were not recognized or used. Did you mistype an argument name?
Backtrace:
  1. EpiModel::netest(...)
 24. rlang (local) `<fn>`(`<rlb_rr__>`)
 25. handlers[[1L]](cnd)
```

which points to these lines in test-netest.R:

```r
  netest_2 <- netest(nw = nw,
                     formation = ~edges + nodematch(r, diff = TRUE),
                     target.stats = c(500, 50, 50, 90, 40, 60),
                     coef.diss = coef_diss,
                     nested.edapprox = FALSE,
                     from.new = "a")
```

It seems like `from.new` is passed through correctly to netest's `...`, so I don't think this is a concern. Yet, is there a way we can stop triggering this warning?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c505447d672`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.