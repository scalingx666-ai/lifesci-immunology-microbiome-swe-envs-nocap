# Issue

**Title:** DEV: replace all biopython useage with cogent3

## Description

[CHANGED] the MinimalFastaParser just returns text objects corresponding to the
    the fasta label line and the sequence data.
[CHANGED] use the SequenceCollection class to output fasta formatted data. The
    write method on that class uses the filename suffix to determine the correct
    formatter.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5de4500413d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.