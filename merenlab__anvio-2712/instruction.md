# Issue

**Title:** Ability to download gene FASTA files for SynGCs

## Description

We have `anvi-export-pan-subgraph` to get everything from the pan-graph databases, but while working with the interface sometimes the user (meren) simply wishes to download all the sequences for all SynGCs in a given bin, that are associated with a region, or the user (meren) simply clicked upon.

This PR adds that function for our users (merens) to benefit from such interface conveniences.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac4332673fe8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.