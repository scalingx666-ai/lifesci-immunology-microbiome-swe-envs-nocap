# Issue

**Title:** Add dcm class support to truncate_sim

## Description

The `truncate_sim` function previously only supported `icm` and `netsim` class objects. This extends it to also handle dcm objects, truncating the epi time series and updating `control$timesteps` and `control$nsteps` accordingly. This got complicated because the change initially treated `dcm` and `icm`/`netsim` objects differently in their handling of `nsteps` within the `plot` and `as.data.frame` functions, so we added a `reset.time` flag that allows the "time zero" to be reset or not at the time step of truncation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f4b5b68e6a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.