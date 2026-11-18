# Issue

**Title:** Bug fix to min_perc_aa filtering.

## Description

Fixed a bad bug with the min_per_aa filtering. The filtering was not working since it was erroneously multiplied by 100 (to get a percentage) before comparing to the filtering criteria which is ultimately passed as a proportion [0, 1].

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8c2eb9613b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.