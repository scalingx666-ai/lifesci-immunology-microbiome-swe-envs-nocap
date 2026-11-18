# Issue

**Title:** Add per-rank DADA2 confidence columns, fix taxonomy string leak into QIIME2

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
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

.

Adds a `<rank>_confidence` column per rank to DADA2's `ASV_tax.*.tsv` and `ASV_tax_species.*.tsv`, alongside the existing overall `confidence` column. Currently only the bootstrap support for the most specific resolved rank is exported, even though `assignTaxonomy` computes it for every rank internally.

Two related fixes found while implementing this, both necessary once the new columns exist:

- `bin/parse_dada2_taxonomy.r`: the `confidence` column was already being folded into the semicolon-joined taxonomy string imported into QIIME2 (`ch_tax`) as if it were a taxonomic rank, corrupting rank-based QIIME2 operations (table filtering, ANCOM, diversity, barplot). Fixed to exclude `confidence`/`*_confidence` from that string.
- `bin/add_sh_to_taxonomy.py` (`--addsh`): derived its taxonomy rank count from a fixed column-count formula, which the new per-rank confidence columns would have silently broken. Now derives rank columns from their actual names instead.

Also closes a real CI gap found along the way: `--addsh` had **zero** test coverage anywhere in the repo (the one place it was referenced, `test_pacbio_its.config`, had it commented out, and that profile also skipped DADA2 taxonomy entirely, so it was never wired to run even uncommented). `conf/test_pacbio_its.config` now also runs DADA2 taxonomy with `--addsh` against the same UNITE database it already uses for SINTAX (`skip_dada_addspecies = true` there, since `addSpecies()` fails on these particular ITSx-extracted sequences for unrelated reasons — `addSpecies()` itself stays covered by the default 16S test).

Both `tests/default.nf.test` and `tests/pacbio_its.nf.test` pass, validated against real pipeline runs (not just lint). `prek run -a` and `nextflow lint .` clean at both the declared minimum (26.04.0) and latest Nextflow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f263461d4a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.