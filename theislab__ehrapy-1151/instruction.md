# Issue

**Title:** Use the times in tem for the time since the last observation in ep.ml

## Description

The GRU, LSTM, GRU-D, TCN, transformer and RETAIN models in `ep.ml` now measure the time since the last observation with the times of the timepoints in `edata.tem[time_key]`, a new argument of `ep.ml.fit` that defaults to the `interval_start_offset` column of ehrdata's loaders, instead of counting timepoints. Irregularly spaced timepoints are therefore spaced correctly, while results on evenly spaced grids are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5678b3426dff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.