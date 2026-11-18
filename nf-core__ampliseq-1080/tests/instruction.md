# Issue

**Title:** Fix SUMMARY_REPORT input file name collision

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
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] `CHANGELOG.md` is updated.

## Description

.

`SUMMARY_REPORT` must accept any user-supplied input files.
If two of them share a file name, the process fails with `input file name collision`.

For example, `--skip_taxonomy` with `--report_abstract` pointing at the `--input` samplesheet fails.
Without `--skip_taxonomy` the bug is usually hidden, because `FILTER_SAMPLES` renames the metadata file first.

Changes:

- `report_abstract`, `metadata`, `input_samplesheet` and `input_fasta` are staged in their own subdirectories via `stageAs`.
- The report shows their base names, so its text is unchanged.
- `test_novaseq`, which already skips taxonomy, now uses its samplesheet as `--report_abstract`.

Verified:

- `test_novaseq` fails without the fix with the error from the issue, and passes with it.
- `test_novaseq` and `test` pass with unchanged snapshots.
- `prek`, `nf-core pipelines lint`, and `nextflow lint` on 26.04.0 and 26.04.6.

**Note for the reviewer:** three other user-supplied inputs, `--report_template`, `--report_css` and `--report_logo`, can collide in the same way.
I left them out to keep this PR small.
They are also riskier to move, since rmarkdown resolves the CSS and logo paths itself.
Happy to open a follow-up issue if you think they are worth covering.

_(Implemented with help from Claude Code.)_

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b760b9d7c00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.