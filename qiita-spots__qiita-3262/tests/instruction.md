# Issue

**Title:** Added prep_id as an optional parameter

## Description

Added prep_id as an optional parameter to
.../study/description/<study_id>?prep_id=<prep_id>.

This will bring up the prep_id workflow page instead of summary information.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3c5ad2d53ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.