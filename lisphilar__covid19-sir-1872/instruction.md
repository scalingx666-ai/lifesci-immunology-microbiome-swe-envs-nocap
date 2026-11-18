# Issue

**Title:** Update Python version support

## Description

This change updates the supported Python versions for the project. It drops support for Python 3.9 and adds support for Python 3.13, following the user's request. The `pyproject.toml`, CI configuration, Conda environment file, and documentation have all been updated accordingly. An investigation was conducted for Python 3.14 support, but it was determined to be not feasible at this time due to dependency constraints.

---
*PR created automatically by Jules for task [7314362216109671265](https://jules.google.com/task/7314362216109671265) started by @lisphilar*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5851d294d363`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.