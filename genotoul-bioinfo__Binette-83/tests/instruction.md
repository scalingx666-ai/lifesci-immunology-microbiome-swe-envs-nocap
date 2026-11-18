# Issue

**Title:** Add a `--quiet` flag to silence INFO logging

## Description

Before quiet mode was the default. but now logging info is the default. If needed the quiet flag can be used to comeback to no info and debug log at all.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ccab47e161f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.