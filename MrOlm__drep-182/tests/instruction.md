# Issue

**Title:** Fix to issue #180: nan in strain_heterogeneity

## Description

Fixes issue #180 by testing for presence of null values in `strain_heterogeneity` column of Gdb. If it finds null values, drops that column, sets the coefficient for strain heterogeneity to zero for purposes of score calculation, and issues a warning.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42d910fcc881`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.