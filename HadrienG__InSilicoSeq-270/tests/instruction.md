# Issue

**Title:** Convert coverage file to read_count dict

## Description

We need to calculate the number of reads that are going to be generated when a coverage_file is used because it depends on the coverage and genome sizes. The n_reads param needs to be accurate because it is used to generate the multiprocessing chunks. This fixes that by converting the coverage_file output to a readcount_dict.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff2282c434d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.