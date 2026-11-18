# Issue

**Title:** Add nodes resource trnaseq sra download

## Description

Add nodes resource to all trnaseq and sra_download workflow rules.
Why: Snakemake's --resources nodes=N flag caps the total threads in use across all running jobs, it is the knob users rely on to limit their cluster footprint. It only works if each rule declares resources: nodes=<thread count>. The trnaseq and sra_download workflows declared threads on their heavy rules but never declared nodes, so --resources nodes= was silently dropped for them and a user (like @ivagljiva) who thought they were limiting CPU usage was not.

What: every rule in both workflows now declares both threads: and a matching resources: nodes= block, consistent with the already-correct workflows (metagenomics, contigs, pangenomics, read_recruitment, phylogenomics, qc).

Note that ecophylo suffers from the same issue. I did not change anything because the ongoing rework #2675.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05e556e5b99a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.