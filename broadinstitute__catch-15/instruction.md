# Issue

**Title:** Add error message explaining why probe count constraint cannot be satisfied

## Description

When the limit on the number of probes to design is not satisfied, this now raises a custom exception (`CannotSatisfyProbeCountConstraintError`) with a message explaining the likely reason. Previously, only an assertion failed and it may have been unclear why. This also raises the exception in the (n>2)-dimensional search, rather than only in the standard search.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `544bce747d47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.