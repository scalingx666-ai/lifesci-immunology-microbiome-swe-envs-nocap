# Issue

**Title:** Fix initial guess to be within bounds

## Description

The initial guess for the higher dimensional search could fall outside
of the parameter bounds. This was causing the error
```
ValueError: `x0` violates bound constraints.
```
by fmin_tnc() in integration tests of param_search.

This commit forces the initial guess to be within the parameter bounds.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2fedca15f921`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.