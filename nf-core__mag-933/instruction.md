# Issue

**Title:** Set concurrent connections for CheckM2 database download

## Description

Our slowest test is almost always `test_alternatives`, and this is entirely because of Zenodo’s transfer speeds when downloading the CheckM2 database. In some cases it takes over an hour (example run: https://github.com/nf-core/mag/actions/runs/19432875847/job/55596172319?pr=932). For reference, a "good" test run takes only around 11 minutes.

Since it’s currently not possible to generate our own CheckM2 test database because of the , and using the S3 mirror isn’t an option because of egress costs when users run tests locally, I propose increasing the number of concurrent connections to 4 when downloading the database.

This shouldn’t be considered abusive to Zenodo, as we’re downloading the same file as usual, just with multiple connections to improve reliability and reduce the impact of exceptionally slow transfers. AFAIK, only the API has rate limits, not the downloads themselves.

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `052e43c3c5b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.