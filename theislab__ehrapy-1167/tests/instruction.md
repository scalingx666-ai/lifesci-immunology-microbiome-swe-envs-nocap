# Issue

**Title:** Remove the utils modules

## Description

Moves the private label/slice selection helper from `ehrapy/_utils_axis.py` into `ehrapy/get/_get.py` and the shared plot parameter docs from `ehrapy/_utils_doc.py` into `ehrapy/plot/_docs.py`, so ehrapy has no utils modules left. Behavior is unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c9169f3d0c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.