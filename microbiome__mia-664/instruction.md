# Issue

**Title:** Abundance classification

## Description

This PR implements abundance classification that is introduced in this paper:

Sizhong Yang, Matthias Winkel, Dirk Wagner, Susanne Liebner, Community structure of rare methanogenic archaea: insight from a single functional group, FEMS Microbiology Ecology, Volume 93, Issue 11, November 2017, fix126, https://doi.org/10.1093/femsec/fix126

New functions include:

- `getAbundant()`: taxa above abundance threshold
- `getLowAbundant()`: taxa below abundance threshold (and between conditionally & permanently rare thresholds)
- `getPermanentlyRare()`: taxa below abundance threshold and below permanently rare threshold
- `getConditionallyRaret()`: taxa below abundance threshold and above conditionally rare threshold

TODO:

- [x] Update documentation
- [x] Clean code and check that everything works
- [x] Add unit tests
- [x] Consider names `getPermanentlyLowAbundant()` and `getConditionallyLowAbundant()`. They are longer but more distinct from `getRare()` which is based on prevalence.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37d5b2144960`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.