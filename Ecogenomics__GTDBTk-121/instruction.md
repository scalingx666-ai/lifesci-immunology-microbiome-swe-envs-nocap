# Issue

**Title:** Intermediate results, FastTreeMP max threads, GZipped genome support

## Description

1. Intermediate results will be written to a subdirectory in the output root, as specified by the config file (default: intermediate_results). []

2. Fixed an issue where FastTreeMP was able to use more threads than specified in the --cpus flag. Resolved by adding a temporary environment variable for OpenMP.

3. GZipped genomes are now supported, re-worked calls to Prodigal by piping FASTA file using subprocess. Prodigal gff output for the best translation table is now cached in memory and then written to disk once the best translation table is identified. No changes were made to FastANI as it supports gzipped genomes (but doesn't say so in the documentation). []

3a. Added a fix where not wrapping the sequence length before passing to prodigal would cause performance to decrease significantly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `704de37e84dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.