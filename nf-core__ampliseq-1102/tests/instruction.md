# Issue

**Title:** Keep the comparison running when a sample has no matches

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

.

The comparison to expected sequences should still report on every sample when one of them has no matches.
Instead, one such sample made `COMPARE_PERFORMANCE` fail and every per-sample output was lost.

- `COMPARE_PERFORMANCE` stopped with `no rows to aggregate` (merge modes `observed`, `expected`, `all`) or `need finite 'xlim' values` (mode `none`) when a sample had no observed sequence matching an expected one. Without matches there is nothing to aggregate, so such a sample is now handled like merge mode `none`, and the scatter plot says that no sequence matches.
- `COMPARE_SEQUENCES` wrote no plots or per-sample tables when every sample was skipped, which failed the process on its required outputs. They are now `optional: true`; nothing downstream uses them.

CHANGELOG: this PR is added to the comparison (#1021, ...) entry in #1109, which edits all of these lines at once to avoid merge conflicts.

Verified:
- A new module test for `COMPARE_PERFORMANCE` (inline inputs, one sample without matches, merge modes `none`, `observed`, `all`) passes with docker and fails on the previous script.
- `compare_sequences.r` run by hand with every sample skipped.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d24c196d9be6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.