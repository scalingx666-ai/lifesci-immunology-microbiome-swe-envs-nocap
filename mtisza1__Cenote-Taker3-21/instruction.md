# Issue

**Title:** fixing pyhmmer syntax, re.sub syntax

## Description

bumping to version `3.4.0`

1. pyhmmer has updated its syntax starting with its `v0.11` release to use `query.name` instead of `query_name`. Therefore, `src/cenote/python_modules/pyhmmer_runner.py` has been updated to avoid this error.
2. forcing pyhmmer `v0.11.0` or higher in main script.
3. fixed `re.sub()` warning in `src/cenote/python_modules/make_sequin_tbls.py`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64171fa63cb1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.