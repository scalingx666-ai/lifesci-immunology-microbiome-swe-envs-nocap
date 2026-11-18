# Issue

**Title:** Add Diat.barcode (rbcL) as a DADA2 reference database

## Description

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository:
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Description

Adds `--dada_ref_taxonomy diat-barcode` (`diat-barcode=15_2`), the DADA2 formatted Diat.barcode rbcL (263 bp) library for diatoms.
.

The database is downloaded from the maintainers' DADA2 dataset (doi:10.57745/SE6GJH).
`bin/taxref_reformat_diatbarcode.sh` removes CRLF line endings and blank lines, adds the final `;` that 17 of 2438 taxonomy strings lack, and derives the addSpecies file from the taxonomy (none exists for v15).
The missing `;` matters: DADA2 treats such an entry as a separate group from the same taxon, which lowered the bootstrap of one test species from 87 to 81.

The new test `tests/diatbarcode.nf.test` classifies seven rbcL ASVs against an 80-sequence subset of the database.
It asserts the eight rank columns, the exact species of six ASVs, and that an ASV with one mismatch gets a species from assignTaxonomy but no exact match.

- The two test files (`diat_barcode_ASV_seqs.fasta`, `diat_barcode_v15_2_tax_assign_dada2_subset.fa`) are not in nf-core/test-datasets yet, so the new test fails until they are added there.
- The maintainers have a newer v16.3, but only as an Excel file; the DADA2 file for it has been requested.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e5ed5c96b9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.