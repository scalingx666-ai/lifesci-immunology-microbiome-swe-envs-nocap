# Issue

**Title:** Fix DataFrame fragmentation warning in _trend.py

## Description

Replaced iterative column insertion with `pd.concat` in `_trend.py` to fix Pandas `PerformanceWarning`. Verified with tests.

---
*PR created automatically by Jules for task [14314398115694557012](https://jules.google.com/task/14314398115694557012) started by @lisphilar*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a585e85eded4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.