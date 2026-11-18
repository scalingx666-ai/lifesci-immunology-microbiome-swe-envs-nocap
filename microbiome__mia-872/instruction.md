# Issue

**Title:** Modify formulas without as.character()

## Description

Replaces as.character() in formula handling with direct modification of the formula, as proposed in #869. Results are unchanged; the functions now also work when formula.tools is loaded. .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4bd520f02074`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.