# Issue

**Title:** make `as.data.frame` resistant to incorrect epi size.

## Description

When restarting huge netsim, sometimes some Epi trackers present in the simulation are not present in the second part of the run (e.g. calibration trackers).

Previously, calling `as.data.frame` on such a `netsim` object would cause an error as some of the trackers would be shorter than the others.

This PR adds a `repair` argument to `as.data.frame` with default value of `"drop"` to simply ignore these trackers instead of stopping. It could be set to `"pad"` as well to left pad the trackers to the correct size with `NAs`.

It also fixes `truncate_sim` that would change the structure of the `sim` object if it contains only one simulation.

#931

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `367cd16ae2c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.