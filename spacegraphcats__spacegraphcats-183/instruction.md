# Issue

**Title:** [MRG] Add query name to contigs signature output by extract_nodes_by_query

## Description

Previously, when outputting each *.contigs.sig file from search, we set the signature name to the filename of the signature itself (which is not very useful). Now set it to `nbhd:` plus the first FASTA header in the query file; this preserves accession information that can be used to get taxonomy, etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62effb248fa0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.