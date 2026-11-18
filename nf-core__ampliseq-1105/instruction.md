# Issue

**Title:** Keep every rank of the winning database when consolidating DADA2 taxonomies

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

.

When several DADA2 databases are consolidated, every rank of the winning database should end up in the result.
Three cases lost or miscounted ranks.

- A database with both `Domain` and `Kingdom`, listed after a Kingdom-only one, had both columns renamed to `Kingdom`. The consolidated `Kingdom` then came from `Domain`, and the real `Kingdom` and `kingdom_confidence` were dropped silently. A synonym now fills its slot only when no column of that name exists.
- `--consolidate_taxonomies most-specific` counted `BOLD_bin` as a rank when the first database is `coidb` or `midori2`. SH and `BOLD_bin` are identifiers and no longer score.
- The tables are read as text, so a rank holding only `F` or `T` is not turned into a logical value. The confidence columns are converted back to numbers.
- `add_sh_to_taxonomy.py` kept the DADA2 bootstrap values of the replaced ranks in the per-rank confidence columns. They are cleared for ASVs that get an SH assignment.
- The `--consolidate_taxonomies score` help text says the bootstrap value is the one of the most specific assigned rank.

Listing a database twice, or a database and its alias (`silva,silva=144`), is already rejected with an error, because the check compares the files each key points to. This PR only adds a test for it.

CHANGELOG: this PR is added to the `--consolidate_taxonomies` (#1062) entry in #1109, which edits all of these lines at once to avoid merge conflicts.

Verified:
- A new module test for `CONSOLIDATE_DADA2_TAXONOMY` (inline inputs, one case per fix) passes and fails on the previous script.
- A new pipeline test for the duplicate-database error passes. It stops before a process runs, so `.nf-core.yml` skips the `versions.yml` snapshot check for it.
- `tests/pacbio_its.nf.test`, which runs the SH assignment, passes with an unchanged snapshot.
- `add_sh_to_taxonomy.py` run on a small fixture: the updated ASV gets blank per-rank confidences, and an ASV without an SH match is unchanged.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d24c196d9be6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.