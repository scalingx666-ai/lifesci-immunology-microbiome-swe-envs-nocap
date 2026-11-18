# Issue

**Title:** Measure survival durations of longitudinal events in time_value units

## Description

The survival models that derive durations from a longitudinal `event_col` measure them in the unit of `edata.tem["time_value"]` when present, so that times to sepsis on PhysioNet 2019 come out in hours instead of seconds.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `701cebd471d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.