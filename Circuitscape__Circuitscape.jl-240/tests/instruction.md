# Issue

**Title:** Fix InexactError in Read Raster

## Description

. In `read_raster`, convert array to Float before proceeding with any array operations so that Int types can be handled without error (particularly in the assignment of -9999.0 NoData values).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ac830b52693`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.