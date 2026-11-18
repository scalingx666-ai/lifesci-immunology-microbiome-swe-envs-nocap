# Issue

**Title:** Fix --skip_barrnap with SUMMARY_TABLE_TAXONOMY

## Description

Addresses reviewer comment 

> workflows/ampliseq.nf:1072 - ch_barrnapsummary.ifEmpty( [] ) combined into a 2-arg map fails with Invalid method invocation call with arguments: true whenever --skip_barrnap is used with any non-Kraken2 classifier (reproduced in an isolated snippet). ifEmpty( [[]] ) fixes it. No test covers skip_barrnap + taxonomy (test_novaseq skips taxonomy too); worth adding.

Confirmed the issue & fixed it. `--skip_barrnap` is now added to `test_glosed` to prevent regression. This changes the snapshot slightly.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41207351b376`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.