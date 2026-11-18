# Issue

**Title:** Fix infinite loop if fasta is empty

## Description

* If the incoming bam file has no alignments to the database, the fasta file is empty
* Since the fasta file is empty, list_size is 0
* passing a list_size of 0 to chunk_list gets stuck in an infinite loop
* This PR returns an empty list of lists; the rest of the code seems well defined enough to output appropriate empty outputs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80dff4f69d1c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.