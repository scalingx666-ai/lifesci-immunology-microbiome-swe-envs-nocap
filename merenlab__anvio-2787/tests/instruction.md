# Issue

**Title:** Hard link `anvi-draw-kegg-pathways` maps into a flat directory, renaming `symlink` to `all_maps`

## Description

`--categorize-files` nests map files in BRITE subdirectories and also gathers every map into one flat directory so they can be browsed without descending the hierarchy. That directory was filled by `os.symlink(os.path.abspath(map_path), …)` — **absolute** targets. Move, rename, or copy the output directory (off a cluster, into a synced folder, into a tarball) and every entry in it either dangles or silently points back at the original tree.

This PR makes them hard links, which store no path at all and survive any move. A file browser also cannot tell them from real files, which matters because browsing is the directory's entire purpose. The directory called `symlink` is therefore renamed to `all_maps`.

```
unified/
├── Metabolism/Carbohydrate_metabolism/ko00010_Glycolysis_Gluconeogenesis.pdf
└── all_maps/ko00010_Glycolysis_Gluconeogenesis.pdf   ← same inode
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c60ca89242f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.