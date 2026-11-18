# Issue

**Title:** Fix ep.pl.timeseries and ep.pl.variable_correlations/variable_dependencies don't support the default .X storage for 3D data

## Description

.
`ep.pl.timeseries` now plots the 3D `.X` by default instead of `.layers["tem_data"]`, like every other function; `ep.pl.variable_correlations` and `ep.pl.variable_dependencies` already default to `.X` on main, and the array type restriction from earlier commits is gone since #1134 made the plot read every array type.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c479b1113fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.