# Issue

**Title:** Merged changes from nf-core template 3.2.1

## Description

Merging changes from nf-core template 3.2.1, essentially bug fixes.

I didnt really understand why the template update attempted to revert the pipeline version from 2.14.0dev to 2.13.0, I rejected most of those changes. However, the ro-crate-metadata.json was changed as well, not sure if that should be reverted.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38a190f9463b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.