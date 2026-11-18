# Issue

**Title:** Allow multiregion analysis without alignment file

## Description

Reorganization of input for custom databases for SIDLE, i.e. multi-region analysis such as 5R.
Now the multiple sequence alignment file for reference sequences has its own parameter and is optional instead of required. That allows much easier usage of custom reference databases, because only taxonomic strings and reference sequences are required.
For this, `sidle_ref_tax_custom` was changed so that it accepts only the taxonomy file instead of requiring 3 files. New params are `sidle_ref_seq_custom` and `sidle_ref_aln_custom` that accept the other 2 files that were previously required by `sidle_ref_tax_custom`. `sidle_ref_degenerates` and `sidle_ref_cleaning` allow easier manipulation of the custom database than before.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e6cf0104f2c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.