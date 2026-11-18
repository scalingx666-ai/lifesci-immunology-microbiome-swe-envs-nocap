# Issue

**Title:** Explain where preprocess_data stores its results

## Description

## Summary
- handle preprocessing results stored as assays or alternative experiments
- retrieve removed-feature metadata from the correct location
- pass the detected preprocessing location to `run_ml()`

## Validation
- `git diff --check`
- affected ML chunks parse successfully
- synthetic assay and altExp storage cases pass
- full mikropml workflow unavailable locally because mikropml is not installed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4546dd437a91`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.