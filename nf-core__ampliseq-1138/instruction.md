# Issue

**Title:** Address 3.1.0 release review: MIDORI2 help text, README wording, CHANGELOG section

## Description

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Description

Small fixes from the review of the 3.1.0 release PR (#1128).
Only text changes, so no tests apply.

- The `--vsearch_lca_ref_taxonomy` help text still named the GenBank270 release on reference-midori.info as the MIDORI2 default. Since #1132 it is GenBank273 from Zenodo.
- The README (and its copy in `ro-crate-metadata.json`) now says the consolidation covers several reference databases and classifiers, matching #1133.
- The #1136 CHANGELOG entry moves from `Fixed` to `Changed`, next to #1134, since it only touches the AWS CI launch action. `Fixed` is now in PR order.

`nf-core pipelines lint` reports three `files_unchanged` failures for workflow files, caused by the installed tools (4.2.1) being newer than the pipeline template (4.1.0). They are not touched here.
There is no CHANGELOG entry for this PR itself, as it only corrects text already described there.

Analysis done with Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4eae4c3ac3bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.