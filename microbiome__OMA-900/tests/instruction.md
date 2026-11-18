# Issue

**Title:** Change miaverse to OMA in overview, refs #895

## Description

Starter PR for #895. Changed 7 prose occurrences in inst/pages/miaverse.qmd from miaverse to OMA, kept URLs/code style, lines <80 chars.
Question for reviewers: line `OMA (MIcrobiome Analysis uniVERSE)` acronym no longer matches — keep as is or need new expansion?
@0xMuluh @TuomasBorman please review, first workflow test per Leo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61c23de087f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.