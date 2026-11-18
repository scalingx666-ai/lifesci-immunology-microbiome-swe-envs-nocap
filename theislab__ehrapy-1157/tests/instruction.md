# Issue

**Title:** Define cohorts by inclusion criteria in filter_observations

## Description

`ep.pp.filter_observations` takes inclusion criteria as pandas query expressions on `obs` columns and variables in `query`, with `tem_names` and `agg` selecting or reducing the timepoints of longitudinal variables, and records every step in a `CohortTracker` passed as `tracker`. Cohort definitions thereby produce CONSORT-style flowcharts without calling the tracker by hand.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29bd9fd4aab6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.