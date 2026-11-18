# Issue

**Title:** Removed spot plot generator

## Description

Spot plots were an initially used functionality that we now hardly ever use, thanks to more sophisticated DQ techniques. It is, however, slowing down the process and messing up functionality. This PR removes the spot plot generator altogether.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e89ba4756a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.