# Issue

**Title:** Pass ancom/ancombc/ancombc2/qiime_adonis_formula as subworkflow args

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
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

Continues #1029/#1032's parameter-handling refactor.

`subworkflows/local/qiime2_ancom.nf` already took `ancombc_formula`/`ancombc2_formula` as explicit `take:` args, but reached into `params.ancom`/`params.ancombc`/`params.ancombc2` directly instead of taking them the same way. Same inconsistency in `qiime2_diversity.nf`, which took `skip_alpha_rarefaction`/`skip_diversity_indices` as args but read `params.qiime_adonis_formula` directly.

Pure plumbing change, no behaviour change — both subworkflows now take all of their flags as explicit arguments, consistent with the pattern the rest of the pipeline is moving toward.

Verified via nf-test (`default.nf.test` covers ancombc/ancombc2/both formula variants/`qiime_adonis_formula`; `sintax.nf.test` covers plain `ancom=true`) — no snapshot changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a56b5c92d544`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.