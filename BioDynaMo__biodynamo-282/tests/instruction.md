# Issue

**Title:** Update OpenCL code with real_t type instead of fixed double

## Description

This PR makes the floating point type of the OpenCL-related code of BioDynaMo be adjustable based on the value of real_t against which BioDynaMo is built.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fa1bad19d71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.