# Issue

**Title:** fastqFilters - add percent of remaining reads

## Description

Hello!
This pull request will add information about percent of remaining reads after filtering with `fastqFilter` and `fastqPairedFilter` to the output status message (if `verbose = T`).

So the message will look like:
`Read in 1500, output 1258 (83.9%) filtered sequences.`
or
`Read in 1500 paired-sequences, output 893 (59.5%) filtered paired-sequences.`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0fb14a11e04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.