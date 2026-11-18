# Issue

**Title:** Pmdtools reference masking fix , sequencetools update

## Description

<!-- markdownlint-disable ul-indent -->
## Changes

- Added masking of reference fasta prior to running pmdtools, when requested.
  - Updated explanation of `pmdtools_reference_mask` parameter in schema.
- Bumped sequencetools `1.4.0.5` -> `1.5.2`

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] Make sure your code lints (`nf-core lint .`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a66d39ffbda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.