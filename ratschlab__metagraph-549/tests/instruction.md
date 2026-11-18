# Issue

**Title:** Support a coordinate-to-accession map to a graph, mapping an annotation label+coordinate to an accession

## Description

An extension to automatically transform query results from column-based to accession/header-based labels

Usage:
#### 1. Construction
After constructing a coordinate-aware annotation, run another annotation step with flags `--anno-filename --index-header-coords` to index the headers and construct the CoordToHeader mapping:
```
metagraph annotate --anno-filename --index-header-coords -i graph.dbg -o annotation file_1.fa file_2.fa ...
```
#### 2. Query
When the CoordToHeader (.seqs) index is constructed (e.g., `annotation.row_diff_brwt_coord.annodbg` + `annotation.seqs`), the mapping is done automatically for the usual query command, e.g.,
```
metagraph query -i graph.dbg -o annotation.row_diff_brwt_coord.annodbg --query-mode matches query.fa
```
To disable the mapping and report the original file-based coordinates/counts/labels, pass flag `--no-coord-mapping`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8c14e566f33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.