# Issue

**Title:** Json schema improvements

## Description

<!--
# nf-core/taxprofiler pull request

Many thanks for contributing to nf-core/taxprofiler!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/taxprofiler/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ NA] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/taxprofiler/tree/master/.github/CONTRIBUTING.md)
- [NA] If necessary, also make a PR on the nf-core/taxprofiler _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [NA] Usage Documentation in `docs/usage.md` is updated.
- [NA] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [NA] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `867c27d1c9ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.