# Issue

**Title:** new utils: picking GC representatives + flag to export them

## Description

A little utils function to get representative sequences from gene clusters. This was originally implemented in another branch #2364, but should be its own PR and merged to master instead.

Includes a new flag for `anvi-get-sequences-for-gene-clusters`: `--representative-sequences`.

Anvi'o picks the represetative using a medoid-based strategy. It discards length outliers and prefers complete (non-partial) gene calls, and select the sequence that is the most similar to the others in the cluster.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dbba14855fc0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.