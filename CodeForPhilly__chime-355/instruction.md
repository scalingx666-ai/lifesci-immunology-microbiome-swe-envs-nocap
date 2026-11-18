# Issue

**Title:** Add disposition type

## Description

Naming of RateDays tuple is causing confusion and would have to be changed when we add PPE parameters for each disposition of (hospitalized, icu, ventilated) or (as a rate of infected, average days in disposition, ppe per day).

Rename to Disposition

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f2d744892c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.