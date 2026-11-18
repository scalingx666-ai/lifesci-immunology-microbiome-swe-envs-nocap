# Issue

**Title:** ENH: Add opacity controller and reorder tabs

## Description

Adds an opacity controller, and the ability to set opacity by a numeric category. Do not merge, there's still tests that need to be added and maybe some better subclassing of the OpacityViewController as it derives most of its features from ScaleViewController.

cc @qiyunzhu

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `604b4e9bece0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.