# Issue

**Title:** Fit the calibration axes of prediction_performance to the predictions

## Description

The calibration panel of ep.pl.prediction_performance ends its axes at the largest predicted probability or observed frequency instead of always spanning 0 to 1. Calibration curves of rare outcomes such as hourly sepsis are no longer squeezed into a corner.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bac1cc3a163f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.