# Issue

**Title:** utilities to make light restart points

## Description

Addition of a `make_restart_point` function.
It created a restart point from a `netsim` object by removing all unnecessary elements and offsetting time and UIDs.
This reduces the size of the restart point as well as the size of the EpiTracker list.

This would for instance allow faster re-calibration as we could used running populations on a regular basis instead of needing the full 60-70 years of burn-in each time

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `367cd16ae2c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.