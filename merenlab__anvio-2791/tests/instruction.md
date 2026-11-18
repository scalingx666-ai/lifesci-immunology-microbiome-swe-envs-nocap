# Issue

**Title:** Panic fixy for GenomeDescriptions

## Description

This PR offers a small fix for an issue that leads to a ConfigError when `anvi-gen-genomes-storage` is run on a list of contigs-db files that are annotated with different functional annotations.

Downstream steps of pangenomics in anvi'o is smart enough to retain only those function annotation sources that are common to all genomes, so it shouldn't lead to an error at this stage.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf8cc5cc6bfa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.