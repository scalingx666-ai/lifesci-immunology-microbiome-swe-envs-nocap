# Issue

**Title:** Switch trend constraint solver to quadprog (removes CVXR dep)

## Description

### Description
This PR resolves the ongoing build failures of `ANCOMBC` on the Bioconductor Linux server (`nebbiolo1`), which was recently discussed on the `Bioc-devel` mailing list. 

The root cause of the build failure is that `CVXR` now depends on `clarabel`, which requires the Rust compiler (`rustc`). Since `rustc` is not currently supported on `nebbiolo1`, `ANCOMBC` fails to build.

Instead of waiting for system-level changes or moving `CVXR` to `Suggests`, this PR completely removes the `CVXR` dependency. I have replaced its single use-case (the `.constrain_est` function used in trend tests) with the `quadprog` package.

### Why `quadprog`?
The `.constrain_est` function solves a Quadratic Programming (QP) problem under inequality constraints. `quadprog::solve.QP` is mathematically identical to the previous `CVXR` implementation for this task but offers significant advantages:
1. **Lightweight & Standard:** `quadprog` is a tiny, Fortran-based CRAN standard, meaning it eliminates the heavy Rust dependency chain and will compile flawlessly on all Bioconductor servers.
2. **Performance:** It is significantly faster for this specific constrained optimization problem.
3. **Numerical Stability:** The new implementation explicitly forces matrix symmetry and adds a microscopic ridge penalty to the diagonal to ensure stability even with poorly conditioned covariance matrices.

### Changes Made
* Rewrote `.constrain_est` in `R/utils.R` using `quadprog::solve.QP`.
* Removed `CVXR` from `Imports` in the `DESCRIPTION` file and added `quadprog`.
* Updated `NAMESPACE` to drop `CVXR` and import `solve.QP`.
* Cleaned up `R/data_sanity_check.R` and `R/ancombc2.R` by removing legacy `CVXR` solver fallback logic (e.g., warnings about `ECOS` vs `OSQP`) and removed the `solver` argument from `trend_control`.
* Updated the package vignettes to remove the obsolete `solver` argument from all `trend_control` code examples.

### Testing
The mathematical equivalence of the new function has been verified locally. It computes the exact same bounded parameter estimates as the previous `CVXR` implementation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ee71a16aae4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.