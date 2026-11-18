# Issue

**Title:** Remove confirmed cases & detection prob

## Description

These are irrelevant to the calculations and only cause user confusion.

"Currently Known Regional Infections" does not impact the projections since we estimate total number of infections using the hospitalized cases. This leads to user confusion. The detection probability by extension is also superfluous. The PR removes both.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `775580757092`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.