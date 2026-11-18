# Issue

**Title:** Add options to label reaction elements and compound circles in `anvi-draw-kegg-pathways`

## Description

`anvi-draw-kegg-pathways` labeled the reaction boxes of standard maps without the option of removing these labels or adding labels for reaction and compound elements on the different kinds of maps. This PR adds `--reaction-labels` and `--compound-labels`. Each takes one or more of `standard`, `overview`, and `global`, or, as a lone value, `none`. The defaults, `standard` for reactions and `none` for compounds, keep the current labels. The following command not only labels reaction elements on standard maps, but also reaction elements on overview maps and compound elements on these two kinds of maps.

```bash
anvi-draw-kegg-pathways --reaction-txt kegg-reaction.txt \
  --reaction-labels standard overview \
  --compound-labels standard overview \
  -o output_dir
```

A reaction element is labeled with KEGG's name for it, which is its first KO, followed by `...` if it stands for several KOs. A compound circle is labeled with its KEGG ID.

This PR also fixes two problems with labels:
- On KO maps, Biopython labeled each box with a reaction twice, once in a pass over entries with reactions and again in its ortholog pass. The box drawn in the second pass hid the first label, but the PDF held both, so a search found every such KO twice. Each label is now written once. EC, RN, and organism-specific maps drawn through `kgml.Drawer` keep the first pass, since it is the only one that labels their entries.
- Boxes and circles too small to see are no longer labeled. This removes the pile of KO labels in the top left corner of maps 04215, 04723, and 05206. It also keeps compound labels off the compound rectangles that anvi'o shrinks to nothing on 00121, 00621, 01052, and 01054.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76f94550eb8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.