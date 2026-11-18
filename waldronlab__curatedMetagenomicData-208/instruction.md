# Issue

**Title:** Combine update combined_metadata and data-raw actions

## Description

This PR combines the actions to update combined_metadata and data-raw to make update-curation.yml. Note that .github/workflows/data-raw.yml is removed and that the curation file is still called sampleMetadata.rda, although it may be changed back to combined_metadata.rda via #196. The action uses cMDC's checkCuration, which is currently failing because it expects column "dataset_name" but has "studyName".

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3316055a7c53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.