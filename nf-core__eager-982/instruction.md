# Issue

**Title:** DSL2: Update input check

## Description

This adds the `bam_reference_id` column to the input TSV, which should be non-NA for BAM input and specify the reference name for the bam. This id is then passed into the `meta` of the bam files as `reference`.
<!--
# nf-core/eager pull request

Many thanks for contributing to nf-core/eager!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/eager/tree/master/.github/CONTRIBUTING.md)
-->
<!-- markdownlint-disable ul-indent -->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eef147980a47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.