# Issue

**Title:** Bedtools process changes

## Description

## Description
- Fixed memory requirements of bedtools coverage.  

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] Make sure your code lints (`nf-core lint .`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e6d09c1337b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.