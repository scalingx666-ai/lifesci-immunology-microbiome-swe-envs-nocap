# Issue

**Title:** Fix `plot.epi.data.frame` when used with restarted

## Description

`df2epi` assumed that the `data.frame` contained `max(df$time)` steps per sim. However, on restarted simulations, the begining of the simulation is trucated.
This PR fixes the computation of the actual number of steps

note: `as.epi.data.frame` would already have check that the `data.frame`  contains the right amount of steps per simulation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07db267aafa5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.