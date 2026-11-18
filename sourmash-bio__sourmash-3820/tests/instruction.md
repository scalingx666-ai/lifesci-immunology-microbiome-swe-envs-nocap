# Issue

**Title:** MRG: upgrade grep behavior: make picklist support clearer and add `-l/--print-matched-names`.

## Description

This PR:
* adds `-l/--print-matched-names` which disables sketch output and just prints the unique matching names
* adds `--no-sigs` as an alias for `--silent`
* adds `--save-picklist` as an alias for `--csv`

TODO:
- [x] add tests for `-l`

Tackles

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `734434dc6fca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.