# Issue

**Title:** Fix Ubuntu-System-CI

## Description

Change number of diffusion iterations, boundary sizes and resolution of EulerDirichletBoundaries. 
Changed number of diffusion iterations for EulerNeumannZeroBoundaries. 
Changed number of diffusion iterations for EulerNeumannNonZeroBoundaries.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `465ba5a6cd28`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.