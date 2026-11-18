# Issue

**Title:** Update to mitigation summary text for `Rt < 1` (issue 155)

## Description

- Changed `display_header` in `src/penn_chime/presentation.py` so mitigation text for values of `Rt < 1` mention halving (vs doubling) and report a positive unit of time.
- Changed `tests/test_app.py` to add `test_mitigation_statement` to test `Rt` values `>= 1` are described as doubling and `< 1` is described as halving.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b26279756273`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.