# Issue

**Title:** Add --proteome-reassign and --proteome-score-mode to proteome clustering

## Description

**Fixes**
- `parseproteomealignments`: write each score row once, after all alignment buckets are counted. Before, rows were written inside the 1e8-entry flush loop, so large alignment DBs got duplicate keys with partial counts. Also check the score allocation before filling it.
- `proteomecluster`: cap biScore at 1. Paralogs in one protein cluster could make the shared count exceed the reference size, and values above 1 were printed wrongly (e.g. `0.1000`).

**New**
- `--proteome-score-mode` (default 0 = current behavior). In mode 1:
  - `proteomecluster` aligns every reference protein of a protein cluster, not only the longest, and counts each member protein once.
  - `easy-proteomesearch` scores the target proteome with the query as reference, the same direction as `proteomecluster`.
- `--proteome-reassign` (`easy-proteomecluster`), like `--cluster-reassign`: a later proteome cluster joins the first earlier cluster whose reference all of its proteomes match.
  - Two searches: reference proteins vs. reference proteins, then candidate references vs. candidate members.
  - New `mergeproteomeclusters` module; it only merges the per-step results.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `503743960fc5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.