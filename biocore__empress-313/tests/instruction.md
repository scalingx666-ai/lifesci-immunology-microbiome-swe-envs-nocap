# Issue

**Title:** Speed up and test sample metadata barplot computations

## Description

.

On the HMP test dataset we've been working with, this went from taking ~10 seconds to draw a sample metadata barplot layer to less than 1 second. The code to compute sample metadata group "frequencies" was modified so that, rather than working on a feature-by-feature basis, all features' frequencies are now computed in a single pass through the BIOM table. Based on discussion with @ElDeveloper about ways to speed this up :)

The code to compute the "frequency map" is now stored in the `BiomTable` class and unit-tested, also.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3ed544cbab8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.