# Issue

**Title:** Update continuum models

## Description

We have reasons to believe that the stencil update used in the `EulerGrid` is not correct and the PR addresses this issue. More precisely, the PR implements to following changes

1. Fix for the `EulerGrid` stencil update
2. Add test for the exponential decay term in the `EulerGrid`
3. Add documentation for API to both `EulerGrid` and `RungeKuttaGrid`
4. Remove `RungeKuttaGrid::DiffuseWithOpenEdge` from code base because it's identical to `Euler::DiffuseWithOpenEdge`
5. Remove `mu` parameter from `RungeKuttaGrid` because the parameter does not appear in the `RungeKuttaGrid::DiffuseWithClosedEdge` code
6. Updates for user-guide reflecting changes 1-5.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ce5c658fb7f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.