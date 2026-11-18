# Issue

**Title:** Level-up ShortRead package dependency version

## Description

This explicitly resolves (through package installation requirements) a difficult to diagnose bug derived from an old version of ShortRead package in Bioconductor. For good measure, Biostrings and data.table were also up-versioned, but the bug-resolving change is the minimum version required for ShortRead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5908b3511e43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.