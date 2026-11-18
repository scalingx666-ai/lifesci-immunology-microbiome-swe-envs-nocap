# Issue

**Title:** Add archive output to appraise

## Description

- [x] Implement in Appraiser
- [x] Add `-p [style output]` argument to appraise with options `standard` (default) and `archive`
  - [ ] Make `output_found_in` another style since it's incompatible with `archive`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `934318be71dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.