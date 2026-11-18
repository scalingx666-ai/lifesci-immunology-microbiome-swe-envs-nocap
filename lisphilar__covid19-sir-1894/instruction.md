# Issue

**Title:** Remove global FutureWarning suppression in dynamics.py

## Description

Removed `warnings.filterwarnings("ignore", category=FutureWarning)` from `parse_phases` method in `covsirphy/dynamics/dynamics.py`. This suppression was applied globally without a context manager. Verified that removing it does not trigger warnings in the current environment.

---
*PR created automatically by Jules for task [2155551580735557553](https://jules.google.com/task/2155551580735557553) started by @lisphilar*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9fd4ec020000`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.