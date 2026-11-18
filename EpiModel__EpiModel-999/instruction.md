# Issue

**Title:** Fix column naming of scalars in mutate_epi

## Description

## Summary

- Fix `mutate_epi()` to replicate scalar constants across all simulations/runs instead of creating a single `"run1"` column
- Column names now match the existing epi structure (e.g., `"sim1", "sim2", "sim3"` for netsim, `"run1", "run2"` for DCM)

Previously, `mutate_epi(mod, threshold = 0.5)` on a multi-simulation netsim would produce a single column named `"run1"`, inconsistent with all other epi elements that have `"sim1"` through `"simN"` columns. This caused issues when converting to a data frame with `out = "vals"`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d851a9c7d66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.