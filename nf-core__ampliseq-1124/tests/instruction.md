# Issue

**Title:** Document that DADA2 bootstraps are not comparable between databases

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
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Description

`--consolidate_taxonomies score` compares DADA2 bootstrap values between databases.
Those values are not comparable between databases, and the parameter help and usage docs now say so.

Two measurements back this up (details in #1113):

- On 199,619 16S ASVs, where SILVA and SBDI-GTDB make the same genus call, SILVA's bootstrap is higher for 54.5% of ASVs and lower for 22.6% (median 0.99 vs 0.91).
- SBDI-GTDB has no chloroplast references, yet gives a genus call with bootstrap of at least 0.8 for 13.3% of confidently identified plastid ASVs.

The help text also says that bootstraps of 1 in several databases give `score` no basis for choosing, and points to `most-specific`, which does not use bootstraps.
No behaviour changes.
Whether to normalise or remove `score` is left open in #1113.

Only help text and documentation change, so no tests were added.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d89534ee1f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.