# Issue

**Title:** Fix truncated epi plot

## Description

`plot.epi.data.frame` with truncated simulation was having an x-axis from 0 to `control$nsteps` but with plot starting at 0.

With this PR, the x-axis goes from `control$start` to `control$nsteps` as it should

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c70798147e22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.