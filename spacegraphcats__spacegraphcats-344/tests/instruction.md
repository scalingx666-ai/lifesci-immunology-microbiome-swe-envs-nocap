# Issue

**Title:** add paired read indexing

## Description

This PR changes read extraction so that (by default) paired reads are output, when _either_ of the reads is found in the search. It does this by labeling paired reads with the same cDBG IDs in `index_reads`. (#284)

This PR also changes the default read output filename to be `reads.gz`, instead of `reads.fa.gz`. (#229)

Fixes 
Fixes 

- [x] allow expect_paired_reads to be set (on by default?), and barf if none are found in first ~100,000 reads or something
- [x] test extraction of reads #284
- [x] address output filename #229

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21d986456448`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.