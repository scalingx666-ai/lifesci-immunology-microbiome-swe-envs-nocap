# Issue

**Title:** Add implied daily growth rate

## Description

- Adds `daily_growth` and `daily_growth_t` instance attributes on `Parameters` class.
- Adds `daily_growth_helper` function to `src/penn_chime/parameters.py` to calculate daily growth rate as a function of doubling time.
- Updates `display_header` function in `src/penn_chime/presentation.py` to display initial and mitigated daily growth rates.
- Adds `test_daily_growth` test to `tests/test_app.py` to test above changes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f0d0461423d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.