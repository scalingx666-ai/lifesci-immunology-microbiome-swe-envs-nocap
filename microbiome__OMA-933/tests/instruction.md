# Issue

**Title:** Rarefaction and ReducedExperiment citations, fix broken citations

## Description

and #926.

## Changes
- **#911 (`transformation.qmd`):** cites Schloss (2026), "Rarefaction is better than robust Aitchison PCA and other compositional data analysis methods at controlling for uneven sequencing effort", *mSystems* 11(10): e00930-26, with one sentence in the rarefaction section, saying that the relative benefits of rarefaction and compositional methods such as robust Aitchison PCA are currently being debated.
- **#748 (`oma.qmd`):** cites the ReducedExperiment package where it is listed among the SummarizedExperiment extensions. The package has no paper; the reference follows its own `CITATION` file (Gisby and Barnes, Bioconductor, DOI 10.18129/B9.bioc.ReducedExperiment).
- **#926 (`transformation.qmd` exercises):** rarefaction exercises already exist in the Alpha diversity (step 5) and Community similarity (step 6) chapters, so the Transformation exercises now point to them instead of repeating them.
- **Broken citations fixed (`transformation.qmd`):** three citations did not exist in the bibliography and rendered as missing references:
  - `@Schloss_2024a` and `@Schloss_2024b` now point to `@Schloss2024rarefaction1` and `@Schloss2024rarefaction2` (Schloss 2024, *mSphere* 9(2) and 9(1));
  - `@McMurdie_and_Holmes_2014` now points to `@mcmurdie2014waste` (McMurdie and Holmes 2014, *PLoS Comput Biol*).
- **`bibliography.bib`:** new entries `Schloss2026` and `R_ReducedExperiment`.
- **Other bibliography problems fixed** (checked with pandoc and against Crossref):
  - duplicated entries removed (Pasolli2017, Love2014, Giliberti2022, Firth1993);
  - `Liu2020` was used for two different papers, so the *microeco* paper now has its own key, `Liu2021microeco`;
  - author fields written as comma-separated lists, which pandoc read incorrectly, are fixed: OMA, Lahti2021bioc, james2013_ISLR (also the author order), Nguyen2022 (also the missing year) and Hang2021.

## Checks
- **References:** all checked against Crossref (title, authors, journal, volume, year) or the package's `CITATION` file.
- **Renders:** `transformation.qmd` and `oma.qmd` render with no citation warnings.

#687 needed no change: the DAA chapter already cites both requested papers (Pelto et al. 2025; Gamboa-Tuz et al. 2025).

Note: rendering `transformation.qmd` twice in a row fails on `devel` because knitr caching is on (fixed in #918).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af5bd544c700`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.