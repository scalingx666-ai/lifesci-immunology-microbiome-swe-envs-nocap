# Issue

**Title:** Fix shiny and plot.icm issues

## Description

Fixes issue in `plot.icm` where `sim.alpha` was turned into logical if `nsims == 1`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3be9642957e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.