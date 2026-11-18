# Issue

**Title:** Suppress validation error log in ODEScenario.append

## Description

Suppressed unnecessary validation error log when calling `ODEScenario.append(end=<date_string>)`.
Previously, the code attempted to validate `end` as an integer (days) first, which failed for date strings and logged an error, even though it subsequently succeeded validating it as a date.
The fix involves a pre-check using `int()` to decide whether to proceed with integer validation or switch to date validation immediately.
Verified that the "validation of end failed" error no longer appears in the documentation notebook execution.

---
*PR created automatically by Jules for task [10189537529757215538](https://jules.google.com/task/10189537529757215538) started by @lisphilar*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c9feccc380e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.