# Issue

**Title:** added collapsing stratified table

## Description

This PR adds support for collapsing a stratified table.

For example, the input profile `phylum_ko.tsv` is like:

Feature ID | Sample 1 | Sample 2 | Sample 3 |
--- | --- | --- | --- |
Actinobacteria\|K00001 | 10 | 6 | 2
Actinobacteria\|K00002 | 4 | 20 | 3
Bacteroidetes\|K00001 | 105 | 0 | 0
Bacteroidetes\|K00003 | 75 | 3 | 0
Firmicutes\|K00002 | 8 | 0 | 0
Firmicutes\|K00003 | 0 | 0 | 2
...|

One wants to collapse KOs into modules using a mapping file `ko-to-module.tsv`, while leaving phyla the same:

```
K00001 <tab> M00123
K00002 <tab> M00123
K00002 <tab> M00456
...
```

One can do (2 means the second field in each feature ID):

```bash
woltka tools collapse -i phylum_ko.tsv -m ko-to-module.tsv -o phylum_module.tsv -f 2
```

The output will be like:


Feature ID | Sample 1 | Sample 2 | Sample 3 |
--- | --- | --- | --- |
Actinobacteria\|M00123 | 14 | 26 | 5
Bacteroidetes\|M00123 | 105 | 0 | 0
Bacteroidetes\|M00456 | 75 | 3 | 0
Firmicutes\|M00123 | 8 | 0 | 0
Firmicutes\|M00456 | 0 | 0 | 2
...|

@droush

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `244e4a0d5cba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.