# Issue

**Title:** Merge branch gctx

## Description

Big update for the Kraken processing workflow! Now uses gctx (from the cmapR package) for internal data processing. Compositional data analysis plots done by default. And improved processing of the default NCBI taxonomy calculated by kraken2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2134b48f508`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.