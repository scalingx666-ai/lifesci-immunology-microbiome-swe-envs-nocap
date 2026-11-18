# Issue

**Title:** to_csv consistency issue fix

## Description

This is an error related to this issue:  – where a `to_csv` call lists columns that do not match existing `pd.DataFrame` column names, `pandas` yields a pretty confusing error referring to `.loc` indexing rather than what's actually wrong. This PR incrementally fixes this.

(DO NOT MERGE YET)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c95b27173f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.