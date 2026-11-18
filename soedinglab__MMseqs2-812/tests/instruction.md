# Issue

**Title:** Fix fasta filename in easy-cluster & easy-linclust usage

## Description

easy-cluster and easy-linclust create _all_seqs.fasta (instead of _all_seq.fasta) files

https://github.com/soedinglab/MMseqs2/blob/2fad714b525f1975b62c2d2b5aff28274ad57466/data/workflow/easycluster.sh#L50

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2fad714b525f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.