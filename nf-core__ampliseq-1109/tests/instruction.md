# Issue

**Title:** Drop CHANGELOG entries for unreleased bugs; update the README summary

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!
-->

## Description

.

The CHANGELOG is relative to the last release, 2.18.0, so its Fixed section should only list bugs that a user of 2.18.0 could have had.
A PR that fixes something never released is listed with the PR that added it.
The README pipeline summary also lacked features of this release.

- Moved #1045 and #1050 from Fixed to the per-rank confidence entry of #1042. They fix regressions from those columns, which are new in 3.0.0.
- Added #1102 to #1108 to the entries of the features they fix: #1102 and #1104 to the comparison, #1103 to Savont, #1105 to `--consolidate_taxonomies`, #1107 to the taxonomy summary tables and #1108 to the per-rank confidences. Doing it here avoids merge conflicts between those PRs.
- Dropped the Fixed entry of #1027 about `lib_layout` in the SBDI `dna.tsv`. The export is removed in the same release (#1083).
- Kept the Fixed entry of #1042: 2.18.0 already folded `confidence` into the taxonomy string imported into QIIME2.
- README pipeline summary: no longer introduced as the steps for paired-end Illumina data; added the Nanopore preprocessing (Porechop_ABI, Chopper), ASV inference with DADA2 or Savont by sequencing technology, the optional comparison to expected results, and VSEARCH/LCA among the classifiers.

The internal version-bump entries (#1018, #1090) are unchanged, in line with the "Bump pipeline version" entry of 2.18.0.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `69f6ba4febc9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.