# Issue

**Title:** Preserve gene caller ids in exported subgraphs

## Description

This PR makes sure that the gene caller ids can be preserved in subgraphs reported by `anvi-export-pan-sbugraph` (but can also be reset to 0 with the flag `--reset-gene-caller-ids`).

The default is good because genes can be tracked in summary reports from the entire pan-graph-db files and/or contigs-db files. Reset can also be good because a fresh start in life have never hurt anyone (except Walter White .. he should have stayed as a chemistry teacher).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75b484464bba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.