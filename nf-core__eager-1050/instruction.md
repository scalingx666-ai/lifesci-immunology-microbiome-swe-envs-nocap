# Issue

**Title:** DSL2: metagenomics testing for malt fixes

## Description

Update for metagenomics dsl2 conversion --
- outputting of malt logs is fixed in parallel execution mode.
- execution of maltextract is fixed in parallel executino mode

NOTE: taxpastamerge currently broken with test data used. will fix next week.
NOTE: linting must be done on dls2-metagenomics branch prior to merging into dev

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad944abdfc9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.