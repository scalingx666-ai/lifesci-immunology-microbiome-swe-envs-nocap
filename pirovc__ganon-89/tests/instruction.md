# Issue

**Title:** Bugfix/nucleotide alphabet

## Description

This PR fixes the issues with alphabets in ganon-build and classify. Now, any character is accepted but anything different than ACTG is converted to N.

Better handling of fastq files was also added. Ganon does not uses the quality values from fastq but now ignores sequences that have incomplete quality values (different lenghts). If the quality values are shorter than the sequence, seqan "eats" the next sequence, so 2 sequences are lost. If the sequence is shorter than the quality value, just the current sequence is ignored.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75baa95b9ec6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.