# Issue

**Title:** Name `anvi-draw-kegg-pathways` map files after their KEGG accession

## Description

`anvi-draw-kegg-pathways` wrote its map files as `kos_00010.pdf`, or `kos_00010_Glycolysis_Gluconeogenesis.pdf` with `--name-files`. That `kos_` prefix is a fossil that was meant to distinguish maps colored by KOs from those colored by other data — a feature that was not yet implemented. With the addition of the compound layer and the availability of KEGG Reaction accession input, the hardcoded 'kos_' prefix is inaccurate.

This PR replaces `kos_#####` with the map's actual KEGG accession, `ko#####`, which is also the name of the reference KGML that anvi'o draws on (`ko00010.xml`). Here are the four output contexts in which the map accession occurs:

```
unified/ko00010.pdf
individual/SAMPLE_1/Metabolism/Carbohydrate_metabolism/ko00010_Glycolysis_Gluconeogenesis.pdf
grid/ko00010.pdf
by_map/ko00010/SAMPLE_1.pdf
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b9f7f4440ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.