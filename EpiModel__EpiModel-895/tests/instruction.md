# Issue

**Title:** overwrite_attrs

## Description

move `overwrite_attrs` from EpiModelHIVp to core epimodel

remove `deleteAttr` that was deprecated in 2.4.0

 #846

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `470ed46397dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.