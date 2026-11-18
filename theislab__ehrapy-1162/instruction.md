# Issue

**Title:** Keep the kwargs-forwarding plots off .raw

## Description

: `ep.pl.pca`, `pca_overview`, `tsne`, `umap`, `diffmap`, `draw_graph` and the `rank_features_groups_*` plots now pass `use_raw=False` to scanpy too, whose default reads `.raw` whenever it is set. All plots therefore read `.X` or `layer` consistently.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29bd9fd4aab6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.