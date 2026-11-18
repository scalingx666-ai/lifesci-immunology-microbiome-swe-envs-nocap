# Issue

**Title:** anvi-draw-kegg-pathways enzymes-txt direct input

## Description

This PR allows `anvi-draw-kegg-pathways` to take `enzymes-txt` directly as input rather than going through a contigs database or metabolic model JSON file. The KOs in the text file are colored in output KEGG pathway map files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2547436eb86a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.