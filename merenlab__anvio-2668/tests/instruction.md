# Issue

**Title:** New Program: anvi-gen-pan-representative

## Description

This PR introduces a new program, `anvi-gen-pan-representative`, which generates a **pangenome-supplemented representative genome** as an anvi'o contigs-db.

The output keeps all contigs from a single representative genome intact, and appends a single supplementary contig that contains one representative gene for every gene cluster in the pangenome that was absent from the representative genome.

The result is a single contigs-db that captures the full gene repertoire of the pangenome.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f1bcfe161a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.