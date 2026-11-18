# Issue

**Title:** Update numpy/scipy requirements

## Description

This makes sure that for both NumPy and SciPy, the version used during testing (as pinned in `requirements.txt`) is the minimum required version (as specified in `setup.py`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af84d317b947`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.