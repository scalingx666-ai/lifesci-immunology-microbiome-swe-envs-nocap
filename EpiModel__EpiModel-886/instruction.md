# Issue

**Title:** Add helpers to work with data.frame of parameters

## Description

Convert from and to data.frame of parameters with `param.net_from_table` and `param.net_to_table`.

Split these code to their own file and add tests.

`param.net_from_table` is part of EpiModel since the use of the `param.df` argument to `param.net` but was not exported. `param.net_to_table` is simply the reverse operation. It's useful to store calibration results back into a csv or xlsx file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6304e8d70c79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.