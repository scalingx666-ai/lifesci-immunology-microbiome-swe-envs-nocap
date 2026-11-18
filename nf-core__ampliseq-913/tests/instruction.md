# Issue

**Title:** Add min boot param

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

This PR adds a new parameter, dada_min_boot, that corresponds exactly with minBoot in DADA2's [assignTaxonomy](https://rdrr.io/bioc/dada2/man/assignTaxonomy.html) method. This parameter specifies a minimum bootstrap confidence (out of 100 trials) needed in order to assign a taxonomic level. This can be helpful in order to filter out assignments for ASVs that are likely too specific. E.g. An ASV was assigned to the incorrect species with confidence 55 (0.55), which is quite low, but was assigned to the correct genus level with confidence 75 (0.75). By setting dada_min_boot to 60 (0.60) in this example, the reported assignment would be to the genus level. Users can adjust dada_min_boot based on their own observations concerning what threshold they begin to see inaccurate assignments.

This also contains a small commit to adjust the order of the read truncation parameters (truncq, trunc_qmin, trunc_rmin, trunclenf, trunclenr) in nextflow.config to match the order they appear in nextflow_schema.json. No functional difference.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10e8c3aa7ea0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.