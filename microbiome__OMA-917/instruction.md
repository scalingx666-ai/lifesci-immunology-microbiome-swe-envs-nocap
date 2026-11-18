# Issue

**Title:** Fix minor bugs that prevented the book from rendering

## Description

This PR fixes small bugs that stopped the book from rendering locally.

## Changes

**`inst/pages/global_association.qmd`**
- Load `vegan` before the Mantel test. `mantel()` and `protest()` come from vegan, which the chapter never attached, so rendering failed with `could not find function "mantel"`.
- Define `mat_mt` in the MiRKAT chunk. `KRV()` and the per-metabolite `MiRKAT()` loop used `mat_mt` but it was never created. It is the standardized metabolite assay transposed to samples × metabolites. The sample order matches `dist_mb`.

**`inst/pages/example_solutions.qmd`**
- Fix prevalence filtering in the Joint-RPCA solution. `getPrevalent()` returns a character vector of feature names, but the result was assigned directly to `mae[["microbiota"]]`, which failed with `'colnames(value)' have no match in 'colnames(x)[[i]]'`. The solution now gets the prevalent feature names, subsets the TreeSE with `tse[features, ]`, and puts the filtered TreeSE back into the MAE.

**`inst/assets/book.scss`**
- Add a missing semicolon before an inline `//` comment in `.navbar-brand-container`. Sass accepts it, but Quarto's internal SCSS parser doesn't, which caused the `Error adding css vars block` warning and dropped the CSS colour variables.

**`.gitignore`**
- One-line addition from an earlier commit on this branch.

## Testing
`global_association.qmd` and `example_solutions.qmd` were each rendered with `quarto render` and complete without errors. The full book was not rebuilt locally.

## Note
`unsupervised_multiomics.qmd` uses `MOFA2::mofa2()`, which exists only in MOFA2 1.23.2 (Bioconductor devel 3.24). Builds on Bioconductor release 3.23 fail with `could not find function "mofa2"`. CI runs on devel, so no code change is needed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d0c4af54099`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.