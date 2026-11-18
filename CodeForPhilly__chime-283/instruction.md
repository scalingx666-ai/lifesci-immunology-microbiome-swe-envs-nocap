# Issue

**Title:** Updates to number input step, min val, and types

## Description

All changes in  `./src/penn_chime/`
**Fixes for issue 269**
* `presentation.py` Updated min value and step for most number inputs.
* `presentation.py` Updated format for float inputs to display as float instead of as int.
* `defaults.py` Change Constants type for doubling_time and relative_contact_rate from int to float
* `settings.py`Change default doubling_time from int to float

**Cleanup**
* Removed unused imports in `presentation.py`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a879ce6a8e86`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.