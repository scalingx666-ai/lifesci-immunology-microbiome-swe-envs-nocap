# Issue

**Title:** Measure qc_metrics and qc_lab_measurements times in time_value by default

## Description

`ep.pp.qc_metrics` and `ep.pp.qc_lab_measurements` now take the times of 3D data from `tem["time_value"]` by default, like the survival models, so longitudinal metrics such as `median_interval` are in the interval unit, for instance days, instead of seconds of `interval_start_offset`, which remains the fallback.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54e337a1c70b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.