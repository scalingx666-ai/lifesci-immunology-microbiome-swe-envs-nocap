# Issue

**Title:** Mention SEtools::se2xls() for exporting a TreeSE to Excel

## Description

Adds a short example of `SEtools::se2xls()` to the export section of the Convert & export chapter (`convert.qmd`). Related: #127.

`se2xls()` writes a `TreeSE` to an Excel file without melting it first: the sample data (`colData`), feature data (`rowData`) and each assay go on separate sheets. This is useful for sharing data with collaborators who work with spreadsheets. The text notes that the phylogenetic tree is not included.

The chunk uses `eval: false`, like the other export examples in this section (feather, CSV), so SEtools is not added to `DESCRIPTION`. The chapter renders.

The rest of #127 (heatmaps via `sechm`, the successor of SEtools' plotting functions) is already covered in the Community composition chapter.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cab13e4a45e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.