# Issue

**Title:** DSL2: Schema and documentation consistency

## Description

Fixing consistency, spelling and grammar of the schema.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11abe6ec594d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.