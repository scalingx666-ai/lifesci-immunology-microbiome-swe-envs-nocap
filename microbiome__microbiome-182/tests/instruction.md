# Issue

**Title:** Merge microbiomeutilites functionality part-1

## Description

Changes in version 1.17.2 (2022-02-03)
+ Merge microbiomeutilites functionality
  * Convert phyloseq slots to tibbles
  * Combine_otu_tax joins otu_table and tax_table
  * Merged add_besthit a fine tuned version from format_to_besthit
  * Merged psmelt2 a fine tuned version from phy_to_ldf
+ Bug fix in transform method alr and tests fixes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f2d16d615bb4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.