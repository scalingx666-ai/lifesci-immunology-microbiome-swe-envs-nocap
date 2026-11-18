# Issue

**Title:** Move format conversion to Importing data; rename chapter 5 to Exporting data

## Description

Moves format conversion from chapter 5 to chapter 4 and renames chapter 5, so that the "Data containers" part reads: Data elements → Importing data → Exporting data.

**Chapter 4, Importing data**
- New section **From other R objects** (formerly "Format conversion" in chapter 5): converting `phyloseq`, BIOM and DADA2 objects to `TreeSE` and back. It sits between "From files" and "Data resources".
- The chapter introduction now mentions both ways of importing.

**Chapter 5, Exporting data** (was "Convert & export")
- Now covers only saving and exporting. The redundant "Exporting" heading is removed and its subsections move up one level: **Save the data container** (RDS files, alabaster) and **Export as table** (TreeSummarizedExperiment, MultiAssayExperiment).
- The exercise is unchanged (convert to `phyloseq` and back, then save).

**Links**
- Section labels are unchanged, so the file and chapter numbers stay the same and existing links keep working, including `#sec-conversions-between-data-formats-in-r` now in chapter 4.
- `oma.qmd` and `tool_list.qmd` now point to the conversion section instead of the whole chapter 5.
- Appendix C heading "Convert & export" → "Exporting data".

Rebased on `devel` after #947 was merged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `282d04b05d22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.