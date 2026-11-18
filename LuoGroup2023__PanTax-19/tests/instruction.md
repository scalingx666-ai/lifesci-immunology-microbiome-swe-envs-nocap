# Issue

**Title:** Update v2.0.0

## Description

+ Update README. `PanTax` can use conda or docker to install the latest version v2.0.0.
+ Fix a bug in `scripts/hcls_select_rep.py`.
+ Adjust the default `fr` parameter of short read single species from 0.43 to 0.3.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `689e0496fa94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.