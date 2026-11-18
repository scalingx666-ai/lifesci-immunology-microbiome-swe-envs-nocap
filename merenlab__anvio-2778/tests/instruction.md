# Issue

**Title:** Codon stats fixes

## Description

This PR contains key fixes to `anvi-get-codon-frequencies` and `anvi-get-codon-usage-bias`.

The flag `--ignore-start-codons` improves the accuracy of synonymous codon frequency calculations for gene sequences containing initiator GTG or TTG, which are otherwise wrongly treated like elongation codons for Val and Leu, respectively.

Genes can now be selected by higher BRITE category annotations, critical for the selection of ribosomal proteins as a reference in the calculation of certain codon usage bias metrics.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78f99179210f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.