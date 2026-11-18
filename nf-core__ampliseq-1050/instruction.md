# Issue

**Title:** Fix confidence columns leaking into summary_report.html taxonomy levels

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
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

.

Fixes a regression introduced by #1042 (not yet released): the DADA2, SINTAX, and VSEARCH-LCA sections of `assets/report_template.Rmd` each derived their "% Classification" breakdown by taking every column except `ASV_ID`/`confidence`/`sequence` and treating the rest as taxonomic ranks. The new per-rank `<rank>_confidence` columns added in #1042 got swept up too, showing as extra bogus levels (`kingdom_confidence`, `phylum_confidence`, ...) in both the text summary and the barplot.

KRAKEN2's section uses a different, unaffected column pattern (no `confidence`/`sequence` columns in its tsv shape) — left untouched.

Validated: an isolated R logic check confirms SINTAX/VSEARCH-LCA are unaffected in practice today (no per-rank confidence columns for them yet, so old and new logic produce identical output), and a full `tests/default.nf.test` run confirms the rendered `summary_report.html` no longer contains `kingdom_confidence`/etc. text.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `36982c79b7c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.