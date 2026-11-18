# Issue

**Title:** Require the strata of cox_ph_adjusted_curves to be in the Cox model

## Description

`ep.tl.cox_ph_adjusted_curves` raises an error when `strata` is neither a covariate nor a strata of `cph`, and its docstring no longer asks to leave it out of the formula, because doing so silently gave every group the same curve.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f33a16026c00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.