# Issue

**Title:** Amplicon performance update and features

## Description

Hi @HadrienG,

This PR brings an updated multiprocessing method that should ideally work for both large input genomes and many small input amplicons. For this, I had to rework the main app.py generate_reads function and split it up for better readability.

The new multiprocessing approach is to calculate the number of reads each CPU needs to generate to get to the requested total, and then pre-assign tuples of SeqIO records and the number of reads to a 'work list'. This then gets distributed to the multiprocessing pool.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b818bbcd7230`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.