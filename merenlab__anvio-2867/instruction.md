# Issue

**Title:** Draw bars in reaction boxes and pies in compound circles from another column in `anvi-draw-kegg-pathways`

## Description

Reaction and compound elements on maps can be filled with color and ringed by a border of another color. This PR lets another column of `kegg-reaction-txt` and `kegg-compound-txt` set the length of a bar in each reaction box and the sweep of a pie in compound circles. The fill still shows one column by its color, while the bar or pie shows another by its extent. A box, for example, can have its fill colored by expression and show gene coverage behind it as a bar. A compound circle can be colored by an isotopic fraction and show the concentration as a pie.

```bash
anvi-draw-kegg-pathways --reaction-txt kegg-reaction.txt \
  --reaction-bar-column coverage \
  --compound-txt kegg-compound.txt \
  --compound-bar-column concentration \
  -o output_dir
```

---
<img width="3433" height="1322" alt="image" src="https://github.com/user-attachments/assets/b3babe32-bc10-4f1f-aca1-012ef13d2f64" />

Part of ko00010 Glycolysis / Gluconeogenesis with reaction bars drawn two ways and made-up values for 36 KOs. Each box is filled by expression and shows coverage with `--reaction-bar-column coverage`, keyed under each panel. Left: in the default `fill` style, the fill color shows only as far as the bar reaches, over a gray track. Right: with `--reaction-bar-style strip`, the fill is drawn whole, and the bar runs along a white strip below the label.

---
<img width="3433" height="1323" alt="image" src="https://github.com/user-attachments/assets/a68bfa10-87b2-49b2-800d-f2cbb6063b89" />

Left: the bars show a made-up log2 ratio, and `--reaction-bar-value-limits -3 3` puts 0 in the middle of each box, so that bars of positive ratios grow to the right and bars of negative ratios to the left. Right: the coverage of the first image, drawn up each box with `--reaction-bar-orientation vertical`. In both panels, KO number labels are dropped, and `label_key_reactions.txt` lists affected boxes; this occurs by default for boxes with signed bars in any direction or vertical bars.

---
<img width="3409" height="1332" alt="image" src="https://github.com/user-attachments/assets/4a8fa2f1-7ad7-4d83-ba1f-a6fd0958417d" />

With `--reaction-slice-by accession` (or `--reaction-slice-by gene`), each column of a box is filled by the expression of one KO (or gene) and shows its coverage. Left: boxes with two or more KOs in the file show their bars side by side, as a small bar chart, and drop their labels. Boxes with one KO in the file keep a horizontal bar and draw their label. Right: with `--reaction-bar-style strip`, each column has a strip of its own below the fill, and every box retains its label.

---
<img width="3041" height="1495" alt="image" src="https://github.com/user-attachments/assets/db1349c7-103a-4ffb-9e22-cfb9b450786a" />

Part of the overview map, ko01200 Carbon metabolism, with made-up coverages of 42 KOs coloring the lines and made-up values for 17 compounds. Left: with `--compound-bar-column concentration`, each pie is colored by a <sup>13</sup>C-labeled fraction and sweeps clockwise from 12 o'clock as far as the concentration, to a full circle at the top of the scale. Citryl-CoA stays white because it doesn't have any values; if it had a concentration of 0, it would be colored gray. Right: the same pies inside the rings of a categorical border column, so that each circle with data shows three columns.

## Features

- `--reaction-bar-column` and `--compound-bar-column` name the column of bar values. It is left out of the search for the value column, so a file with a bar column and no value column colors its fills by presence. A row can leave its bar cell empty. Bar values can be negative, except in a compound file, since a pie has no zero line.

- Bars are drawn in the reaction boxes of standard maps and pies in the compound circles of standard and overview maps, inside any ring. Reaction lines and global maps show neither. A compound file with a bar column always colors its fills, so on global and overview maps those fills replace the colors that compounds take from touching reactions.

- In the default `fill` style, a bar runs from 0 in the color of the fill, and a thin dark line marks its end. The rest of the box shows a gray track, so that a bar of 0 differs from a box without data. With `--reaction-bar-style strip`, the fill is drawn whole, and the bar is dark on a white strip along the bottom of the box.

- The bar scale always includes 0, and limits that leave it out are refused. The scale of pies starts at 0. Where a map's scale has values on both sides of 0, bars grow both ways from a gray zero line. A value past a limit reaches the end of its box or fills its circle, and the key marks that end `≤` or `≥`.

- `--reaction-bar-orientation vertical` runs bars up their boxes. Without the option, bars are horizontal, except in sliced boxes of the `fill` style, whose bars are vertical where two or more of the element's KOs or genes have bar values in the file. A `fill`-style box with a vertical bar or on a signed scale drops its KO label, and `label_key_reactions.txt` lists such boxes.

- With `--reaction-slice-by`, each column of a box shows the bar of its own KO or gene, and `slice_key_reactions.txt` gains a `bar` column. Columns can be sized by `--reaction-slice-weights`, so a strip's extent must be read against the width of the column, and a filled bar varies in width independently of the bar value.

- On a map that shows bars or pies, an element with a fill and no bar value is left uncolored, and a warning counts such elements, since a whole fill would read as a full bar or pie. A box of the strip style keeps its fill instead, without a dark strip or a warning.

- Every option that reduces or summarizes the fill has a bar version, such as `--reaction-bar-gene-aggregation` and `--compound-bar-sample-summary`, and so do the value limits. Bar aggregations default to `mean`, and bar summaries, which refuse `count`, `count_continuous`, and `membership`, have no default. The `unified` map of a file with samples, and the map of each group, therefore show bars or pies only where a bar summary is given.

- Bars and pies get keys of their own, such as `bar_key_reactions.pdf` and `bar_key_compounds_samples.pdf`, labeled with the column and `(bar)`. Players of `--animate-files-by-map` show them beside maps that can show bars or pies.

- `--reaction-color none` and `--compound-color none` are refused with a bar column, since a bar or pie needs a colored fill. Bar options are refused in runs of contigs databases, a pangenome, or a reaction-network JSON.

## Additional notes

- `keggmapping.TXT_CHANNEL_ROLES` describes the fill, border, and bar channels in one table, from which the Mapper builds channels and the CLI runs its guards.

- A display list, `kgml.Graphics.glyph`, describes the interiors of boxes and circles, which `SlicedKGMLCanvas` draws, and `Graphics.slices` now serves lines only.

- A glossary at the top of `keggmapping.py` defines the terms of the module.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e438050dcd7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.