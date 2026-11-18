# Issue

**Title:** Bump the tutorials to e03d6c0 and ehrdata to 6ede6dc

## Description

Moves the tutorials to the version without workarounds for the fixed bugs and ehrdata to main, whose mimic_iv_meds, write_h5ed and annotate_codes fixes the data tutorial now relies on. The pyproject dependencies of ehrdata are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81efa4a033ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.