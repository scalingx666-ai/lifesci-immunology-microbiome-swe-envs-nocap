# Issue

**Title:** Dash callbacks refactor

## Description

Resolves 2 tiny bugs introduced by the new develop rebase hidden under widget combinations.

* Table rendering if `NaN`s are present
* Using date first hospitalized instead of doubling time (set to `None` in widget) now converts strings to dates

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `677f96c87152`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.