# Issue

**Title:** add sample and group support for anvi-draw-kegg-pathways with enzymes-txt input

## Description

The `enzymes-txt` file now supports an optional "sample" column, specifying, for example, that KO rows are from the *E. coli* or *K. pneumoniae* genome, or KOs are from Sample 1, 2, or 3. Samples can correspond to sample groups in `groups-txt`, e.g., KOs from groups of related genomes, or KOs from daytime versus nighttime samples. This mirrors sample and group coloring from multiple contigs databases and pangenomes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ab46f17ef36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.