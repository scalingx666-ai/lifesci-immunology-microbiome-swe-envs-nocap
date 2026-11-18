# Issue

**Title:** Reject unsupported Savont inputs with clear errors

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

.

Savont should only run on data it supports, and fail with a clear message when it cannot.
Several unsupported cases ran without an error or failed with a Savont usage error.

- `--multiregion` with Savont (including the nanopore default) and `--asv_calling savont` with paired-end Illumina now stop with an error. Before, Savont treated each `sample_region` copy as a sample, and received two files per sample.
- When every sample is removed after Chopper (`--ignore_failed_trimming`), the pipeline stops with a message naming `--min_read_counts` and `--skip_chopper`. Before, `SAVONT_ASV` ran without reads and failed with `the following required arguments were not provided: <FASTQ/FASTA>...`.
- The Chopper read-count join uses `meta.id` instead of `meta.sample`. `meta.sample` repeats across regions, and `join` then pairs by arrival order.
- `SAVONT_ASV` gets an explicit `pooled` input. Pooling a single sample used to drop `--pooled-samples`, because Nextflow stages one file as a path, not a list.
- A duplicate `tax_agglom_max` line in `conf/test_savont_independent.config` is removed; the later line already won.

CHANGELOG: this PR is added to the Savont (#1026, ...) entry in #1109, which edits all of these lines at once to avoid merge conflicts.

Verified:
- New pipeline tests for the three errors (`savont_incompatible`, `savont_multiregion`, `savont_nosamples`) pass. They stop before a process runs or after Chopper, so `.nf-core.yml` skips the `versions.yml` snapshot check for them.
- `savont.nf.test` and `savont_independent.nf.test` pass with unchanged snapshots.
- The empty-input failure was reproduced on `test_savont` with Chopper `-q 60`.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `587bd426735c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.