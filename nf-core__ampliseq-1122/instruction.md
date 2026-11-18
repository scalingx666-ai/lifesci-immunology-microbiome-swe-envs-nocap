# Issue

**Title:** README: say what the metro map does not show; remove BOLD Plantae leftovers

## Description

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Description

Docs only.
The README now says what the metro map does not show, as discussed in #1121, and the "Pipeline summary" list gets the optional steps that were missing (length and codon filtering, ITS extraction, Sidle, consolidation, differential abundance, functional prediction, summary tables).

Also removes the `CITATIONS.md` entry and `bin/taxref_reformat_plantae.sh` of the BOLD Plantae databases, which were removed in 2.15.0 (#894) and are referenced nowhere.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b48f6ff59d1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.