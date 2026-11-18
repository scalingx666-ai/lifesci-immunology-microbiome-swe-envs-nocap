# Issue

**Title:** Renamed sampleMetadata back to combined_metadata

## Description

Rename sampleMetadata back to combined_metadata. I left some remnants of sampleMeta, such as data-raw/sampleMetadata.R, but tried to change instances where we refer to the data frame.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bbb3abfdb6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.