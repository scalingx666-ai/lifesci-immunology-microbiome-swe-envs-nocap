# Issue

**Title:** Implement skip abundances arg

## Description

Add argument to recover to skip CoverM abundances post-binning.
Last unskippable rule that isn't necessary for large-scale binning efforts.

- [x] Tested in dryrun
- [x] Tested manually in test_integration.py
- [x] Tested manually with real samples

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d925a011f632`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.