# Issue

**Title:** Fix BiocCheck metadata and citation warnings

## Description

## Summary

- Expand the package description in `DESCRIPTION`.
- Update the minimum R dependency to R 4.6.0.
- Add two DOI-backed publications to `inst/CITATION`.
- Add the missing return-value documentation to the package-level help page.

## Validation

Tested with:

- R 4.6.1
- Bioconductor 3.24
- BiocCheck 1.49.30
- Ubuntu 26.04.1

Results:

- `devtools::document()` completed successfully.
- `knitr::knit(input = "README.Rmd", output = "README.md")` completed successfully.
- `R CMD check`: `Status: OK`
- `BiocCheck`: `0 ERRORS | 0 WARNINGS | 13 NOTES`
- `git diff --check`: clean

The remaining BiocCheck notes are advisory and outside the scope of the three warnings addressed by this pull request.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08323b4ff10d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.