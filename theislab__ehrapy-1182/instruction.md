# Issue

**Title:** Drop the redundant legend of violin plots grouped by integer categories

## Description

`ep.pl.violin` with `groupby` no longer draws a legend that repeats the x axis, which appeared for integer categories such as a 0/1 treatment flag.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6942458f88a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.