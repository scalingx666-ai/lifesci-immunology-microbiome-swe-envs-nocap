# Issue

**Title:** Validate comparison inputs and pick the highest-level observed profile

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

.

Comparison inputs that cannot be used should stop the pipeline with a message.
Two combinations were silently ignored, and the observed profile could be the wrong file.

- `--expected_abundances` without `--expected_sequences` now stops with an error. Before, nothing ran.
- `--expected_profile` together with `--skip_taxonomy`, `--skip_qiime`, `--skip_qiime_downstream` or `--skip_abundance_tables` now stops with an error. Before, there was no observed profile, so the profile comparison did not run.
- The observed profile is the file with the highest level number. It was the last file in lexicographic order, so with `--tax_agglom_max` of 10 or more, `rel-table-10.tsv` sorted before `rel-table-2.tsv`.
- Reverse-complement matches are documented, not filtered. vsearch runs with `--strand both`, which suits reads of either orientation, so an observed sequence that is the reverse complement of an expected one counts as a match.

CHANGELOG: this PR is added to the comparison (#1021, ...) entry in #1109, which edits all of these lines at once to avoid merge conflicts.

Verified:
- A new pipeline test for the two errors passes. It stops before a process runs, so `.nf-core.yml` skips the `versions.yml` snapshot check for it.
- `savont.nf.test` and `savont_independent.nf.test`, which use `--expected_profile`, pass with unchanged snapshots.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c72ac9ab6ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.