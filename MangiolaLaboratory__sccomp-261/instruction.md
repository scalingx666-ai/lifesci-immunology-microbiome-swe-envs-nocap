# Issue

**Title:** Enhance documentation for restricted environments

## Description

- Added guidance in README.md and introduction.Rmd for using `sccomp` in restricted or read-only environments, including instructions for setting a custom cache directory for Stan models.
- Introduced `cache_stan_model` parameter in `sccomp_boxplot` function to allow explicit cache directory specification.
- Added unit tests for cache handling in restricted environments.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `abe77bcc97b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.