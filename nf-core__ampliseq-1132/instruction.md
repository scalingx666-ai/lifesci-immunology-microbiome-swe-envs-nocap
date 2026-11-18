# Issue

**Title:** Download MIDORI2 databases from Zenodo, remove them from --dada_ref_taxonomy

## Description

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Description

. The MIDORI2 downloads on `reference-midori.info` return 404, so `midori2-co1` could not be used.

**Please note: this removes MIDORI2 from `--dada_ref_taxonomy`.**
DADA2's `assignTaxonomy` cannot use the MIDORI2 CO1 files: GB273 has 243k (`DADA2`) to 858k (`DADA2_sp`) distinct taxonomy strings, and `assignTaxonomy` handles at most 65,535.
With a synthetic reference, 40,000 taxa classify correctly, while 70,000 and 100,000 return the wrong taxon for the first query without an error.
The real file fails with `Memory allocation failed`, also with 90 GB.
The old DADA2 URL (GB250) is dead and GB250 is not on Zenodo, so nothing that worked is lost.
`midori2-co1` and `midori2-co1=gb250` are no longer accepted by `--dada_ref_taxonomy`; the docs table and a footnote say why.
A genus-level DADA2 reference (58,627 strings for GB273) would fit and could be a later follow-up.

For `--sintax_ref_taxonomy` and `--vsearch_lca_ref_taxonomy`:

- The three `midori2-co1` entries now download the Zenodo zips: `midori2-co1` (GB273, new default), `midori2-co1=gb273` and `midori2-co1=gb270`.
- A new format script extracts the CO1 file from the zip; the task fails if there is none.
- Checked on Nextflow 26.10.0 that the Zenodo URLs stage with `file()`.
- Ran `-profile test_fasta,docker` with SINTAX and VSEARCH-LCA against `midori2-co1` without `--ref_taxonomy_storage`: staging, extraction, formatting and classification worked.
- New module tests build a small zip inline, with another gene and a `total/` variant as decoys, and a zip without CO1.

The zips are 0.4 to 0.5 GB for a ~100 MB file, so the usage docs recommend `--ref_taxonomy_storage`.

This branch is on top of #1129 (it reuses its `format_taxonomy_sintax` test file), so the diff shows #1129's commits until that is merged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca28287b770f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.