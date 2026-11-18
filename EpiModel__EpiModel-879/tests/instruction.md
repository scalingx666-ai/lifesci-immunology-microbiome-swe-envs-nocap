# Issue

**Title:** add a control check for `nsteps`

## Description

previoulsy if `Inf` was passed to `control$nsteps`, the error would occur in the first call to `set_epi` due to the wrong value passed to `rep(NA, nsteps)`.

This PR makes the error explicit

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7622d3b2962`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.