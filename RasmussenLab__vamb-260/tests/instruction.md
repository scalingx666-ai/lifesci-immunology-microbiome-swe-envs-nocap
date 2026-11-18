# Issue

**Title:** Validate taxonomy and abundance paths early

## Description

* Validate existence of paths used in TaxonomyOptions
* Validate that BAM files are sorted on instantiating AbundanceOptions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce9ab88501d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.