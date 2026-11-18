# Issue

**Title:** Script to add essentiality data to 9th column of CDS lines

## Description

<!--
# ebi-metagenomics/mettannotator pull request

Quick script to read in essentiality data from a tsv and insert a new key-value pair into the 9th column of a GFF file. The essentiality data was provided to us by our collaborators, and we modify CDS lines with this additional data when there is a match in the coordinates. For now, the input essentiality data is a summary. It may later be a requirement to include medium information in which case this script may need an update.

python script.py <gff_file> <essentiality_file> <output_gff_file> <not_matched_file>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed04a80bace7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.