# Issue

**Title:** Fix NumPy generic timedelta deprecation warning

## Description

Replaced the deprecated `np.timedelta64(tau, "m")` with `pd.Timedelta(minutes=tau)` in `covsirphy/dynamics/ode.py` to resolve a `DeprecationWarning` regarding implicit unit conversions with bare integers in newer NumPy and Pandas versions.

---
*PR created automatically by Jules for task [1171299102545770932](https://jules.google.com/task/1171299102545770932) started by @lisphilar*

## Summary by Sourcery

Bug Fixes:
- Resolve DeprecationWarning by switching from np.timedelta64 with bare integer minutes to pd.Timedelta in ODE date conversion helper.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `605e0ab2270c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.