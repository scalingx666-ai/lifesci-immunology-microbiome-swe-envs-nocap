# Issue

**Title:** ord_plot: use vegan sumev attribute for axis % labels

## Description

. Thanks @erikrikarddaniel for the report.

`ord_plot()` computed axis-label percentages as `eig[axes] / sum(eig)`. For ordinations that keep only the first k axes, that inflates every percentage, because the shares of the kept axes always sum to 100%. Now the total comes from the `sumev` attribute of `vegan::eigenvals()` when it is present, as `summary.eigenvals()` does, and falls back to `sum(eig)` otherwise.

- New internal helper `ordExplainedVar()` in `R/ord_plot.R`.
- No change for ordinations made by `ord_calc()`: none of them set `sumev`, and the existing vdiffr snapshots are unchanged. (`decorana` does set it, but `ord_plot()` shows no percentages for DCA or NMDS.)
- Tests: the helper with and without `sumev` (including `NA`), and agreement with vegan's "Proportion Explained" for a clr PCA and for `decorana`.
- Checked locally (not in CI) against the issue's example, `ecolongr::el_rda(k = 3)` on dietswap clr at Genus rank. That object's `eigenvals()` method sets `sumev = tot.chi`. Its labels now match the full PCA: PC1 25.3% and PC2 10.6%, compared with 58.8% and 24.6% before.
- Minor docs improvements to `?ord_plot`: the Details section now explains how axis-label percentages are calculated, two typos are fixed, and the duplicated `tax_lab_style` see-also link now points to `constraint_lab_style`.
- Version bump to 0.13.2 and a NEWS entry.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Ordination axis-label percentages now use the total variation reported by the ordination when available, including for truncated PCA results from other packages.
  * When that total is unavailable, percentages are calculated from the sum of the eigenvalues. Results for ordinations created with `ord_calc()` remain unchanged.
* **Documentation**
  * Clarified how axis percentages are reported for PCA, PCoA, RDA, and CCA, and that NMDS and DCA axes are shown without percentages.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9fa48f7bf99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.