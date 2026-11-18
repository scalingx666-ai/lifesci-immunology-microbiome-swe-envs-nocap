# Issue

**Title:** Clarify `dist_bdisp` vs `vegan::betadisper` defaults and add parity coverage

## Description

This pull request updates the microViz package to version 0.13.1 and focuses on improving documentation and clarity around the `dist_bdisp` function, especially regarding its default behavior and alignment with default changes in the `vegan` package. It also rerenders the readme, and adds a new test to ensure consistency with `vegan::betadisper()`.

**Documentation and Functionality Clarifications:**

* Expanded and clarified the documentation for the `dist_bdisp` function in both the R source (`R/dist_bdisp.R`) and the manual (`man/dist_bdisp.Rd`). This includes detailed parameter descriptions, return value explanations, and a new note emphasizing that `dist_bdisp` still defaults to `method = "centroid"`, while recent versions of `vegan::betadisper()` default to `type = "median"` [[1]](diffhunk://#diff-788531b944ee563234e4138b6c6ef4ef3f3e08269a2f8718eb57162c917f815bL3-R38) [[2]](diffhunk://#diff-a657b2691ad47831c6a02c65b8976efb3d81ec671a93627a233316745f178238L16-R57) [[3]](diffhunk://#diff-51920e95310ebfbc1ae31709f3b95f89afffbf4f1a6e38e8b2b406e2fb6197eaR1-R4).
* Improved the argument handling in `dist_bdisp` by using `match.arg()` for the `method` parameter, ensuring only valid values ("centroid" or "median") are accepted.

**Testing:**

* Added a new test to confirm that `dist_bdisp` produces results matching `vegan::betadisper()` when the `type`/`method` arguments are aligned, improving reliability and consistency.

**Maintenance and Metadata Updates:**

* Bumped the package version to 0.13.1 in `DESCRIPTION`.
* Updated citation counts and example output timestamps in `README.md` and `README.Rmd` to reflect recent usage and software versions [[1]](diffhunk://#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5L20-R20) [[2]](diffhunk://#diff-72778b58969c8ca8268402860b0e003e3d213a26c812bc9f9b928395c284c99fL19-R19) [[3]](diffhunk://#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5L153-R153) [[4]](diffhunk://#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5L319-R320) [[5]](diffhunk://#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5L345-R346) [[6]](diffhunk://#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5L437-R442) [[7]](diffhunk://#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5L455-R494).

These changes improve user understanding of the `dist_bdisp` function, ensure compatibility with upstream changes in dependencies, and keep the package documentation and examples current.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5254a80a7cb8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.