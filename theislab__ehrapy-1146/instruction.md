# Issue

**Title:** Add ep.pl.trajectories for group means over time

## Description

`ep.pl.trajectories` plots the mean of longitudinal variables over time with a confidence band for every group of observations, e.g. the Glasgow Coma Scale of PhysioNet 2012 patients who died and survived. Only the plotted variables are densified or computed, so it works on dask and large data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5cdc12d84594`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.