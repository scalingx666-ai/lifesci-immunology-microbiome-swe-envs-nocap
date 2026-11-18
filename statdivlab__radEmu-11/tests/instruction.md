# Issue

**Title:** Add ability to use `radEmu` on a `phyloseq` object

## Description

This pull request adds `phyloseq` to the suggested packages, adds the ability in `emuFit()` to take in a `phyloseq` object as the argument `Y`, adds a test of this functionality, and adds data from the Wirbel et al. meta study in the format of three data objects (a covariate table, a count table, and a taxonomy table) that can be combined to make a `phyloseq` object.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a50d944a94c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.