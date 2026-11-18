# Issue

**Title:** Add documentation for score_test, resolve TODOs in emuFit, create central function for creating j_ref

## Description

Documentation now exists for score_test, and emuFit TODOs should be resolved. get_j_ref is now called whenever we want to choose j_ref for optimization or testing -- this way if there is an issue we can edit this function instead of tracking down the 3-4 places in code j_ref is chosen

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43ec98ae3ef1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.