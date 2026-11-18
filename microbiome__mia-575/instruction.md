# Issue

**Title:** fix tree agglomeration in agglomerateByPrevalence

## Description

As mentioned in  agglomerateByPrevalence returns a TSE object with `rowTree = NULL`.

This PR removes the class checking and class conversion from TSE to SCE that removes the tree.

With this modification, the tree is returned and agglomerated if `agglomerate.tree = TRUE`.

```
data("GlobalPatterns")
tse <- GlobalPatterns
tse <- agglomerateByPrevalence(tse, rank = "Phylum", agglomerate.tree = FALSE)
rowTree(tse)
```
>Phylogenetic tree with 19216 tips and 19215 internal nodes.
>Tip labels:
  549322, 522457, 951, 244423, 586076, 246140, ...
Node labels:
  , 0.858.4, 1.000.154, 0.764.3, 0.995.2, 1.000.2, ...
>Rooted; includes branch lengths.

```
data("GlobalPatterns")
tse <- GlobalPatterns
tse <- agglomerateByPrevalence(tse, rank = "Phylum", agglomerate.tree = TRUE)
rowTree(tse)
```
>Phylogenetic tree with 67 tips and 66 internal nodes.
Tip labels:
  549322, 173903, 368907, 51888, 591769, 249529, ...
Node labels:
  , 0.858.4, 1.000.21479, 0.946.619, 0.953.588, 0.940.473, ...
Rooted; includes branch lengths.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24d2263a95e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.