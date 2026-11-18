# Issue

**Title:** Remove sigma layer from the model

## Description

An old bug in Vamb constrained the value of logsigma to be positive due to a softplus operation on the logsigma. However, the optimal logsigma values for all VAEs are negative, which meant logsigma was essentially fixed to zero. Therefore, we can simply remove the sigma layer and directly substitute a zero.

A better long-term solution might be to properly add a sigma layer and fix the bug, but unfortunately, Vamb has been optimised around the bug for so long that this would be a bigger operation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b9f1e8fd6f1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.