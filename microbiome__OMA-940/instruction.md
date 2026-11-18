# Issue

**Title:** Verify and fix bibliography references

## Description

Verifies every reference in `inst/assets/bibliography.bib` and fixes the problems found. One commit per kind of fix.

## How the references were verified
- **Entries with a DOI** (174): each DOI was looked up in Crossref and the title, year and first author compared. All are real publications matching their entries; the only problems were malformed DOI fields.
- **Entries without a DOI**: journal articles were searched in Crossref by title, and the less certain matches confirmed by looking up the papers' DOIs. Books and software entries were checked by hand.
- **Result:** no fabricated or mismatched references were found.

## Fixes
1. **Malformed DOI fields** (7 entries): a URL prefix or a `/FIGURES/n` suffix broke the reference links.
2. **Author fields parsed incorrectly**:
   - `Kembel2010`, `Chao1984`, `Chao1992`, `Kurtz2015`, `Pasolli2017` and `Ernst2020` had given names read as family names (e.g. "W, Kembel Steven").
   - `R_BiocGenerics`: the team name was split into a given and a family name.
   - `Argelaguet2018`: "et al." was rendered as part of the name; it is replaced with the full author list.
3. **Preprints replaced by published versions**: `Schloss2023` → `Schloss2024rarefaction1` (mSphere) and `Karwowska2024` → `Karwowska2025` (Microbiome) in the transformation chapter. The sentence quoted from Schloss is also in the published abstract.
4. **Duplicated MOFA entry**: `Arpelaguet2017` merged into `Argelaguet2018`.
5. **Uncited duplicates removed**: `Callahan2016workflow`, `Das2020`, `Lun2020`, `pelto2024`, `patchwork2022`.
6. **Hill 1910**: the URL pointed to Wikipedia; it is replaced with the page range.
7. **Capitalization protected in titles**: Pandoc converts titles to sentence case and the citation style then title-cases them, so unprotected words were rendered wrongly (e.g. "Microeco: An r Package…", "miaSim r Package", "Vegan: Community Ecology Package"). The following are now wrapped in braces, while other words stay unprotected so the style can still adjust their case:
   - proper nouns such as R, Bioconductor, Quarto, R Markdown, S4, Bayesian, Illumina, Parkinson, Oregon and California;
   - package names written in lowercase, such as microeco, vegan, phyloseq, knitr and scater.

## Testing
- **Bibliography:** 260 entries, parsed by pandoc with no warnings and no duplicate keys.
- **Citations:** every key cited in the book exists in the bibliography.
- **Rendering:** the transformation and OMA chapters render with no citation warnings.
- **Casing:** all entries were rendered with pandoc citeproc and the titles checked for wrongly cased names.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `14b8a92e220a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.