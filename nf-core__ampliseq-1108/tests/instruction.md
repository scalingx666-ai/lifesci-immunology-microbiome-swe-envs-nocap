# Issue

**Title:** Leave per-rank confidences and the source database out of phyloseq objects

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

.

The taxonomy table of the R objects should hold taxonomic ranks.
It also held the per-rank confidence columns and `database` of a DADA2 taxonomy table, which phyloseq treats as ranks.

- `PHYLOSEQ` and `TREESUMMARIZEDEXPERIMENT` drop the `<rank>_confidence` columns and `database` when they read the taxonomy table.
- `confidence` and `sequence` stay as before, so existing output does not change beyond the new columns.
- `docs/output.md` says what is left out of the R objects and where it remains.

CHANGELOG: this PR is added to the per-rank confidence (#1042) entry in #1109, which edits all of these lines at once to avoid merge conflicts.

Verified:
- The module's R code run in its container on a small DADA2 table gives the ranks `Kingdom`, `Phylum`, `confidence`, `sequence`.
- The TreeSE module's R code run in its container on a small DADA2 table gives `rowData` columns `Domain`, `Phylum`, `confidence`, with the sequences in `referenceSeq`.
- `tests/taxonomy_hash.nf.test`, which builds both objects, passes.
- `tests/default.nf.test`, which builds the DADA2 and QIIME2 phyloseq objects, passes with an unchanged snapshot.
- There is no automated check of the object's content, because nf-test cannot read R objects.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Output Documentation in `docs/output.md` is updated.
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d24c196d9be6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.