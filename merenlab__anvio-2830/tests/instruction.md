# Issue

**Title:** Fix `anvi-draw-kegg-pathways` to read gene cluster KOs from pangenomic reaction network JSON files

## Description

`anvi-draw-kegg-pathways --reaction-network-json` drew nothing from a JSON made from a pangenome with `anvi-get-metabolic-model-file`. A genomic JSON keys each gene's `annotation['ko']` by KO ID. A pangenomic JSON lists gene clusters instead. Each has one KO, given as `{'id': ..., 'modules': ..., 'pathways': ..., 'hierarchies': ...}`. The reader took the keys in both cases. So it found four "KOs" ('id', 'modules', 'pathways', 'hierarchies') and drew 0 maps.

The reader now takes `annotation['ko']['id']` where that field is present, and the keys otherwise.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de1b44805cc6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.