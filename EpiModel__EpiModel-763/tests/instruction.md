# Issue

**Title:** create a generic padded_vector function

## Description

refactor `set_epi` and `add_epi` to use a generic `padded_vector` function that can be used by `nwstats` or `transmat` for instance.
Also put `epi` by default to `NA_real_` as they are more often numeric than logical

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a3dc83197c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.