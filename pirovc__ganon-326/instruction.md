# Issue

**Title:** ganon v2.4.2

## Description

- Small fixes and renaming of `--report-type` to avoid confusion
  - `reads` -> same
  - `matches` -> same 
  - `dist` -> same
  - `abundance` -> will now only correct for genome size (old behavior of `corr`)
  - `dist+abundance` -> (new) will perform basic re-distribution and correct for genome size (old behavior of `abundance`)
  - `corr` -> removed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ac58a5460c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.