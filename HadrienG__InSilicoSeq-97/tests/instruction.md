# Issue

**Title:** Fix out-of-bounds error

## Description

This pull request provides a simple solution to the problem described in #96. If the computed index is greater than the length of the sequence, append `A`. Otherwise, append the requested nucleotide.

I'm assuming this problem doesn't occur much with whole genome sequences, since it's very rare for a read both to have an indel and line up right at the end of the chromosome. However, when sequencing short amplicons in draft mode this case occurred with high frequency.

There are probably more elegant solutions to this problem. One could:
- draw a random base instead of `A`
- draw a base from some distribution of nucleotide composition
- append Illumina adapters or other technical sequences to the end of the genomic sequence

But for now, this is a simple solution that allows InSilicoSeq to run without barfing on amplicon sequences.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b675de47050`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.