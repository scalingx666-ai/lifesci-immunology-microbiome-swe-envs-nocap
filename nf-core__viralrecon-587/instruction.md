# Issue

**Title:** migrate lib/.groovy to utils_nfcore_viralrecon_pipeline

## Description

## PR description

This PR refactors several helper functions out of `lib` and into the corresponding subworkflows, so the logic is kept closer to where it is used. It also adds validation for required parameters in `viralrecon.nf`.

### Subworkflow refactor

* Moved `checkprimers` and MultiQC TSV-related logic from `lib` to the subworkflow.
* Moved `getcol` and `countLinesFromFile` from `lib` to the subworkflow.
* Moved `checkContigsInBed` and `getNextcladeFieldMapFromCsv` from `lib` to the subworkflow.
* Moved `getNumVariantsFromBCFToolsStats` from `lib` to the subworkflow.
* Moved Illumina workflow helper functions from `lib` to the subworkflow.

### Parameter validation

* Added validation for required parameters in `viralrecon.nf`.

### Related Issues

 — Move workflow-specific helper functions out of `lib` and validate required parameters.


<!--
# nf-core/viralrecon pull request

Many thanks for contributing to nf-core/viralrecon!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `924a212c50b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.