# Issue

**Title:** do not allow defined vars to act as snakemake wildcards

## Description

This was an issue for running the extract_reads workflow. {catlas_dir} was evaluated as a snakemake wildcard, instead of the value defined at the top of the Snakefile. 

2nd minor change: label_reads rule did not need the `contigs.fa.gz` file as input.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34974a80d58d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.