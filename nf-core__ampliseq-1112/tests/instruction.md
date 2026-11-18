# Issue

**Title:** Compare score consolidation at the deepest rank all databases assigned

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

`--consolidate_taxonomies score` should pick the database that is most confident about an ASV.
It picked the database that stopped at the highest rank instead.

DADA2's bootstrap only falls with rank depth.
`score` compared each database's confidence at its own deepest assigned rank, so a genus assignment at 0.6 lost to a family assignment at 0.9, even when it was more confident at family.
Raised by @d4straub in #1105.

- `score` now compares confidences at the deepest rank that every remaining database assigned.
- Databases tied there are compared again at their next shared rank, and a deeper assignment wins a tie.
- Remaining ties go to the database listed first, as before. Bootstraps of unassigned ranks are ignored.
- The `--consolidate_taxonomies` help and `docs/output.md` describe the new rule.

On `test_multidb`, 165 of 347 ASVs change winner, all to a deeper assignment (GTDB now wins 283 instead of 142).

Whether bootstrap values are comparable between databases of different size is left for a separate issue.

CHANGELOG: added to the `--consolidate_taxonomies` (#1062) entry. #1109 adds #1105 to the same line, so whichever merges second gets a one-line conflict.

Verified:
- Four new `CONSOLIDATE_DADA2_TAXONOMY` module tests pass. Two fail on the previous code, one fails on a variant that compares only once, and one would fail if the deepest assignment simply won.
- `multidb_score`, `multidb_mostspecific` and `multidb_mixedranks` pass with unchanged snapshots; `multidb_score` snapshots file names only.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] Output Documentation in `docs/output.md` is updated.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c72ac9ab6ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.