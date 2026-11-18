# Issue

**Title:** Add metadata filter

## Description

This is adding the ability to filter the data for downstream analysis with the metadata sheet. This could be helpful to remove negative control samples meant for Decontam or subset the data for e.g. PCoA plot and the like. As a side effect, when samples are not passing preprocessing (and that is intentionally ignored by setting specific parameters) then the pipeline will not complain that the samples are in the metadata sheet but not in the other data tables.

CI test `test_failed` (3/14) was modified via  to test for that case.

Due to the change from 4 to 3 samples to downstream analysis, beta diversity statistics analysis cannot be performed, leading to less files produced. Additionally, the count tables change their content (and therefore md5sum).

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [x] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bcefe645fd43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.