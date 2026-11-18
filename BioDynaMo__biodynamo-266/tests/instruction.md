# Issue

**Title:** Improve the time series collection API

## Description

Encourage the usage of `bdm::experimental::Counter` and `bdm::experimental::GenericReducer`
over their function counterpart.
The class TimeSeries can combine multiple reduce-functors together, resulting in a much 
cache-friendlier data access pattern and thus improved performance.

`TimeSeries::Update` calculates reducer collectors first. This means their results can be used in 
function-style collectors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `857a63aec46f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.