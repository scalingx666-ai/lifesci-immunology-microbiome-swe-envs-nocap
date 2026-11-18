# Issue

**Title:** Fix paired-end --input_folder and small release docs errors

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

Small fixes found while reviewing the 3.0.0 release PR (#1091).

- `PARSE_INPUT`: the paired-end branch started with a bare `ch_reads` instead of `ch_reads =`, so `--input_folder` with paired-end reads failed with `No such variable: ch_reads`. No test uses `--input_folder`.
- CHANGELOG: the `--iontorrent` row of the breaking-change table now maps to `--sequencing_type iontorrent` (was `nanopore`).
- Parquet summary tables: missing values were the string `NA`, and numeric-looking sample names (`1`, `2`) became integers in `ampliseq.counts.parquet`. `DUCKDB_TABLE2PARQUET` now passes `nullstr='NA'` and reads `sample` as text for the counts table. `barrnap_domain` is documented as `NA`, not blank.
- Docs: `--place_aln`/`--place_model` are `--pplace_aln`/`--pplace_model`, `VSEASRCH` is `VSEARCH`, the "Compare to expected" link points at the right heading, and the per-sample comparison is stated to ignore `--expected_sequences_mismatches`.
- `silva=144` is listed in the `--dada_ref_taxonomy` help text, and DuckDB is added to `CITATIONS.md`.

No CHANGELOG entry: the fixed behaviour only exists on `dev`.

Verified by running `PARSE_INPUT` standalone on two paired-end fixtures (it fails at `main.nf:33` without the fix and emits both pairs with it), and by writing a small table to Parquet with DuckDB 1.5.5 using the new options (`sample` is text, missing values are NULL).

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d24c196d9be6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.