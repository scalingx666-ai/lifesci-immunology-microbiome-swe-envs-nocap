# Issue

**Title:** add --match-per-kmer option in classify workflow

## Description

Metabuli allocates memory for storing matches between query k-mers and reference k-mers.
As default, ```--match-per-kmer``` is 4, and enough memory to store four matches per one query k-mer is allocated.
Four matches per k-mer are enough in most cases.
But we added an option to adjust the value because it is reported that four is not enough when input reads are populated with low-complexity sequences.
We already added ```--mask``` option in ```classify``` to prevent matches from low-complexity regions.
When you meet overflow!!! signal even with the ```--mask 1```, set ```--match-per-kmer``` > 4.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `941d27441158`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.