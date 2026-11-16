# Issue

**Title:** Add cache_stan_model parameter to relevant functions and update docum…

## Description

…entation

Introduced a new parameter, cache_stan_model, to functions including sccomp_estimate, sccomp_replicate, simulate_data, and sccomp_remove_outliers. This parameter specifies the cache directory for compiled Stan models, ensuring version isolation. Updated documentation and tests to reflect these changes, ensuring proper functionality and default settings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12beb07c50b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.