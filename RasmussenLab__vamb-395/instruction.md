# Issue

**Title:** Enforce well-behaved taxonomy annotations on tax construction

## Description

Several parts of TaxVamb's and Taxometer's handling of taxonomies have some implicit assumptions which are not checked. Perhaps the restrictions could be lifted, but for now, let's check it when we parse the input files. In particular, taxons are referred to by their name in the code, which means they must be unique.
To enforce it, we enforce that:
* A taxon with a given name must always appear on the same rank
* A taxon with a given name must always have a parent with the same name I believe this should be sufficient to ensure the tree is well-formed.

May fix #391

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc43b4550e37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.