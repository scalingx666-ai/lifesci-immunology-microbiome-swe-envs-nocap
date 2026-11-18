# Issue

**Title:** Added formatting params and a module

## Description

- `acc2taxid.map` is generated again during `build`
- `--lineage` parameter for `classify`
- `--extract-format` for `extract`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `238873e53adc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.