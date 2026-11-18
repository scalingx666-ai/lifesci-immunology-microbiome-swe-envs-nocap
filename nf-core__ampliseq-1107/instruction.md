# Issue

**Title:** Document what the summary tables hold, and sanitise the PPLACE table name

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

Part of #1099.

The `passed_*` and `ampliseq_accept` columns of the taxonomy summary tables look like per-filter pass/fail flags for every ASV.
In these tables they are always `TRUE`, because only ASVs that survive the filters are in the table.

- `docs/output.md` now says that taxonomy is assigned to the ASVs that remain after clustering and all filters, so removed ASVs have no row and `passed_*` and `ampliseq_accept` are `TRUE` in every row. It also says that a filter's column exists only if the filter ran, that `ampliseq.counts` is taken before clustering and the filters, and that it is only written with `--asv_calling dada2`.
- `--pplace_name` is free text and went unchanged into the file name `ampliseq.taxonomy.PPLACE.<name>.tsv.gz`. `SUMMARY_TABLE_TAXONOMY` now replaces everything but letters, digits, `_` and `-`. The file names of the other classifiers are unchanged.

Not in this PR: publishing the per-ASV annotations for all ASVs, filtered ones included, as a separate summary table. That would make the columns useful, but it is a new output, so it is left for a decision on #1099.

CHANGELOG: this PR is added to the taxonomy summary tables (#1063) entry in #1109, which edits all of these lines at once to avoid merge conflicts.

Verified:
- A new module test for `SUMMARY_TABLE_TAXONOMY` checks the file name for a name with a space and a slash; it fails without the change.
- The same test file checks that a header-only QIIME2, PPLACE and DADA2 table give a header-only summary table.
- The PPLACE test names (`test_pplace`, `PPLACE`) are unchanged, so no snapshot changes.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Output Documentation in `docs/output.md` is updated.
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d24c196d9be6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.