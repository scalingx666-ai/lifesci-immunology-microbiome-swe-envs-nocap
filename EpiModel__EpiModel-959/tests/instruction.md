# Issue

**Title:** Set VECLIB_MAXIMUM_THREADS

## Description

## Summary

Fix segfault in `netsim()` when running multi-core simulations (`ncores > 1`) on macOS, specifically after a single-core run in the same R session.

## Problem

On macOS, `netsim()` with `ncores > 1` dispatches simulations via `foreach %dopar%` → `doParallel` → `mclapply`, which forks the R process. Apple's Accelerate framework (the default BLAS provider on macOS) uses Grand Central Dispatch (GCD) for multi-threaded linear algebra. GCD does not support process forking — when a forked child calls into Accelerate, the process segfaults:

```
*** caught segfault ***
address 0x110, cause 'invalid permissions'

Traceback:
 1: predict.lm(object, newdata, se.fit, scale = 1, ...)
 2: predict.glm(acts.mod, newdata = x, type = "response")
 3: predict(acts.mod, newdata = x, type = "response")
```

Because the workers crash, `mclapply` returns NULL results, and `saveout.net()` then throws a misleading secondary error:

```
Error in if (dat$control$save.run) { : argument is of length zero
Warning: scheduled cores 1, 2 did not deliver results
```

### The ordering dependency

The crash does **not** occur if multi-core `netsim()` is the first call in a session. It occurs when a single-core `netsim()` run precedes the multi-core run. This is because:

1. Single-core `netsim()` calls `predict.lm()` → triggers BLAS matrix operations → **initializes GCD's thread pool in multi-threaded mode**
2. The GCD thread pool state persists for the lifetime of the R process
3. A subsequent multi-core `netsim()` forks via `mclapply` → child processes inherit the already-initialized GCD state → the GCD threads are in an invalid state in the forked children → segfault

This is the standard interactive workflow (run a quick single-core test, then scale up), which is why it reliably triggers.

### Likely trigger

This appears to have been triggered by a recent Xcode / Accelerate framework update that enforces stricter fork-safety on GCD dispatch queues. The same code path was always technically unsafe in forked processes, but older Accelerate versions tolerated it. Linux (OpenBLAS/MKL) is unaffected.

## Fix

Set `VECLIB_MAXIMUM_THREADS=1` at the **top** of `netsim()` on macOS, before any code path (single-core or multi-core) runs. This prevents Accelerate from ever initializing a multi-threaded GCD pool, keeping the process fork-safe for the entire session. The environment variable is restored via `on.exit()` when `netsim()` returns.

This is safe and arguably more efficient for multi-core runs — each forked worker runs on its own core, so per-worker multi-threaded BLAS would only cause contention. The fix is a no-op on Linux/Windows.

## Testing

Verified on macOS (Apple Silicon, R 4.5, post-Xcode update):

| Sequence | Without fix | With fix |
|----------|------------|----------|
| Multi-core only | ✅ works | ✅ works |
| Single-core → multi-core | ❌ segfault | ✅ works |
| Multi-core → single-core → multi-core | ❌ segfault | ✅ works |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2608b7782313`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.