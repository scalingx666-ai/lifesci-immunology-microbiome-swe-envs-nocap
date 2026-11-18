# Issue

**Title:** Fix continuum models

## Description

- Reintroduced l[] factors to Euler Diffusion
- Corrected build target 'run-check'
- Fixed build target 'coverage-build'

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9589c6e2924b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.