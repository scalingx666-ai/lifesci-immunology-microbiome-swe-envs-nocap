# Issue

**Title:** Pileupcaller paths fix

## Description

This PR corrects the staging of input bam files for the genotyping_pileupcaller process. 
Avoids rare cases where binding of volumes failed within singularity and caused the process to fail.

The issue was revealed when upstream changes were made to fix endorspy caching errors.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core lint .`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2418f64a8cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.