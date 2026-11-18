# Issue

**Title:** Modify default call to pmap when paralellizing

## Description

This addresses the discussion in #236.
By default, `core.jl` makes use of `pmap`. However, this is problematic if the user wishes to parallelize Circuitscape at a higher level than the pairs level. I change the solver functions to use `map` by default and only use `pmap` when the users sets `parallelize` explicitly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d44a41a20be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.