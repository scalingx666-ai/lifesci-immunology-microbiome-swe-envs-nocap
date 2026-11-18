# Issue

**Title:** Add ability to automatically download sequences for a taxonomy

## Description

This PR adds an option to specify input in the form of an NCBI taxonomy ID. When specified this way, CATCH will fetch all accessions (genome neighbors) for the taxonomy, download sequences of those accessions, and use them as input.

This adds the `ncbi_neighbors` module to make calls to NCBI's Entrez system. To use this feature, the format for input datasets to [`design.py`](https://github.com/broadinstitute/catch/blob/master/bin/design.py) is `download:TAXID`. TAXID is an NCBI taxonomy ID. This PR also updates the README to describe this feature and changes the main example to use it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf97305e06af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.