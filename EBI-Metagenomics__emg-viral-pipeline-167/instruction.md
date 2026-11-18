# Issue

**Title:** Bugfix/write gff missing contigs when user provided proteins

## Description

Fix KeyError for contigs missing from assembly in write_viral_gff
Contigs present in annotation TSVs but absent from the assembly FASTA
caused a KeyError in three places in write_gff()

This happens when the user provide proteins, as the proteins could be
for contigs that were filtered out by the length filter VIRIfy use.
I've added a bit of code to make it fail if all the contigs are
discarded as this would a problem.

Adds a regression test with some file fixtures.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `758442860a61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.