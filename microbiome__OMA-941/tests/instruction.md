# Issue

**Title:** Fold long plotting code

## Description

.

Folds long code blocks that only create or format plots, as OSTA does, so that the analysis steps and figures stand out while the code is one click away. Uses Quarto's `code-fold`, with "Show the plotting code" as the link text.

## Folded (9 blocks)
- **Alpha diversity:** plots of all indices; Shannon index with pairwise p-values.
- **Community similarity:** MDS/NMDS comparison; correlation of principal coordinates with and without rarefaction; Shepard plot; PCoA coloured by dominant taxa; the same split by group.
- **Unsupervised multi-omics:** MOFA variance explained.
- **Machine learning:** ROC and PRC curves.

## Left unfolded
- **Contain analysis steps:** NeatMap (`runPCA()`, `getNeatOrder()`), ML predictions and feature importance.
- **One function call that is the point of the example:** `plotBoxplot()` in differential abundance, the mediation plots.

Blocks were selected by finding code blocks with at least 12 lines of code that mostly call plotting functions, then reading each one.

## Testing
- Alpha diversity renders with the two folded blocks and the link text "Show the plotting code".

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72edd00f5761`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.