# Issue

**Title:** Update test_gis.py to fix strict type checking failure

## Description

Updated `tests/test_gis/test_gis.py` to fix a type checking error in `test_area_name` by using a list instead of a tuple for the geographic layers argument. This change aligns with strict type checking requirements. Additionally, ensured `from __future__ import annotations` is not used, respecting the project's Python 3.10+ target. Verified changes by running tests locally.

---
*PR created automatically by Jules for task [14777225767110145961](https://jules.google.com/task/14777225767110145961) started by @lisphilar*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f71ed6810b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.