# Issue

**Title:** Fix Greengenes2 SINTAX database and remove Diat.barcode before release 3.1.0

## Description

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Description

Two fixes for release 3.1.0, found by running the SINTAX conversion for every database.

**Greengenes2 SINTAX gave an empty database.**
`taxref_reformat_gg2.sh` writes `assignTaxonomy.fna.gz`, but `taxref_reformat_dada2_to_sintax.sh` read only `assignTaxonomy.fna`.
The awk error was lost in the pipe to `gzip`, so the task exited 0 with an empty `sintaxdb.fa.gz` and every ASV went unclassified.
The converter now reads either file and fails on errors and on an empty result.
A new module test, `modules/local/format_taxonomy_sintax/tests/main.nf.test`, covers the Greengenes2 chain, plain input, rank letters, the more-than-nine-ranks failure and empty input.

**Diat.barcode is removed from the release.**
Nextflow cannot stage the download URL: the Dataverse endpoint answers HEAD with a redirect to a presigned S3 link that rejects HEAD (403), so `file(<url>)` fails with "Unable to access path" on 26.04.0 and 26.10.0.
This affects `--dada_ref_taxonomy` and `--sintax_ref_taxonomy`.
The CI test used a subset from test-datasets, so the real URL was never fetched.
The database can be added again once there is a stable download location.
The metro map is restored from 3.0.0 with the version set to 3.1.0, so it no longer shows the label.

Checked by running all SINTAX databases except MIDORI2 (its download URL returns 404 and is unchanged from `master`): all formatted databases are well-formed.
`prek run -a` and `nf-core pipelines lint --release` pass.
The full CI test suite is pending.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b260f8d9b755`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.