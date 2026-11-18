# Issue

**Title:** GloSED database incorporation

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ not needed ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [ not needed ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ not needed ] `README.md` is updated (including new tool citations and authors/contributors).

## Issues closed

would close #1008 adding a new database to the list of approved databases.


## Change notes

I've added in a new database option: GloSED. This is mainly through the addition of two new scripts, one to download the required files and one to reformat them appropriately. I have also made minor edits to the main pipeline to allow GloSED as an acceptable database option, integrate it if chosen, and cite it appropriately. 

I have added a test profile for glosed to test the database. 

Though GloSED does include SH numbers I have not included the code to process them and so the GloSED database does not currently work with addSH. Though this is reasonably possible to do if the need arises.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53d81c56b6f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.