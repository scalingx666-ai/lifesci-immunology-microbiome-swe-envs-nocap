# Issue

**Title:** anvi-reorient-genomes should catch genomes with no alignment

## Description

I recently realized that the program simply explodes if the `fasta-txt` includes genomes that have no alignment with one another. This happened while working with a bunch of cyanophages that were 'very closely related' lol. PHAGES.

This PR makes sure that before anything real happens, every genome is benchmarked against the reference to make sure the user can decide how to proceed if there are any alignment snafus.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2daf02e47127`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.