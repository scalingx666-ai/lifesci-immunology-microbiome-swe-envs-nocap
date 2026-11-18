# Issue

**Title:** Extend DiffusionGrid interface for full gradient information

## Description

This PR makes the `DiffusionGrid::GetGradient` more flexible. It allows retrieving the absolute value of the gradient such that modelers can use the full information of the gradient, e.g. define behaviors that are only executed if the gradient is stronger than a certain threshold. 

Furthermore, the PR introduces a UnitTest to verify that the gradients are computed correctly by comparing an analytic and numeric solution.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `248f4c30b391`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.