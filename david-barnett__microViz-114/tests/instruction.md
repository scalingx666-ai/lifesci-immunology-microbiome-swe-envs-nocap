# Issue

**Title:** fix: fixed erroneous taxon ordering that occurred if comp_barplot tax_level is set to "Taxon"

## Description

This occurred in the tax_rename documentation!
https://david-barnett.github.io/microViz/reference/tax_rename.html

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23a30ec873d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.