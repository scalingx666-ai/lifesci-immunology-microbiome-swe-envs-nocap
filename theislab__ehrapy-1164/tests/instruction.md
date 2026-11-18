# Issue

**Title:** Read variables of 3D data at their baseline and derive survival times from longitudinal events

## Description

`ep.get.obs_df`, and with it the survival and regression models, the causal estimators and `ep.pl.scatter`/`catplot`/`ols`, now take variables of 3D data at their first non-missing value (or another `statistic` in `obs_df`), and the survival fitters derive the duration and event from a binary longitudinal `event_col`. This makes `ep.tl.kaplan_meier(edata, event_col="SepsisLabel")` work on PhysioNet 2019 without a new function or stored columns.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `306dcbd483d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.