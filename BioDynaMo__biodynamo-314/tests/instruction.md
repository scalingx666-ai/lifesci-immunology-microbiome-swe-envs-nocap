# Issue

**Title:** Add `DataTransformer` for `TimeSeries::Data`

## Description

The new transformer class can be used to transform the (x,y,y_min,y_max) values of the time series entries. This version does not work in place; it copies the data and, in the process, transforms it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80e047817326`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.