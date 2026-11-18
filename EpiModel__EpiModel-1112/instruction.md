# Issue

**Title:** Trim the 2.7.0 NEWS entry to one line per change

## Description

Cuts the section from about 3,700 to 1,100 words. Breaking changes keep only the migration steps, and related merge.netsim, restart, and small fixes are combined.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2515758d738`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.