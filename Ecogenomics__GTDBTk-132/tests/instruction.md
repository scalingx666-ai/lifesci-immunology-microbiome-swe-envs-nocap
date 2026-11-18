# Issue

**Title:** Added option to use a custom taxonomy file when rooting a tree.

## Description

This is useful if the user wished to outgroup on a set of user genomes that don't have GTDB taxonomy strings. It also applies if the user wishes to create a tree without any of the GTDB reference genomes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdf4b6be9888`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.