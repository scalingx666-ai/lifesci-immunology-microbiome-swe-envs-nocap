# Issue

**Title:** store CAZyme family names as functions in anvi-run-cazymes

## Description

Just like the name suggest: instead of having no entry for 'function' for most CAZyme entries, we copy the accession, which is the CAZyme family name, into the function table.

The motivation came from using `anvi-compute-functional-enrichment-across-genomes` and the results did not make sense at all, but also did not really failed because 9 CAZyme entries had proper functions and the programme only used these 9 for the enrichment.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c980d4f90ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.