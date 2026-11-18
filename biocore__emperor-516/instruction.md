# Issue

**Title:** ENH: Improve axes labels font size

## Description

The size of the font in the axes labels is now determined according to
the range of the datapoints (like with the sphere sizes).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `022a689a4556`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.