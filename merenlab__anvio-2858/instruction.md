# Issue

**Title:** Fix map grid labels for contigs databases and pangenomes in `anvi-draw-kegg-pathways`

## Description

Since c8a24d819, map grids drawn from contigs databases and pangenomes have been mislabeled; this is now fixed.

- In grouped runs, the per-group colorbars read "source count" instead of "database count" or "genome count".
- The 'unified' panel of a pangenome grid read "all" instead of "pangenome".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fdee0de03f45`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.