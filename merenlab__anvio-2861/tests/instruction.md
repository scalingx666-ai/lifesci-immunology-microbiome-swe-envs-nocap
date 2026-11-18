# Issue

**Title:** Color the borders of reaction boxes and compound circles by a second column in `anvi-draw-kegg-pathways`

## Description

Map elements can be filled with color, or colors for slices. This PR allows another column of values from `kegg-reaction-txt` and `kegg-compound-txt` to be colored in a border ring independently of the fill. The ring lies just inside the outline of each reaction box and compound circle, and is separated from the fill by a thin line, demarcating similar fill and border colors that would otherwise blend into each other. The fill of a box, for example, can show gene coverage and the border gene detection; the fill of a compound circle can show, in an overview map, the average value imparted from the reaction lines that touch it, and the ring a measured concentration.

```bash
anvi-draw-kegg-pathways --reaction-txt kegg-reaction.txt \
  --reaction-border-column status \
  --reaction-border-value-type categorical \
  -o output_dir
```

<img width="3220" height="598" alt="1_glycolysis_fill_and_border" src="https://github.com/user-attachments/assets/74575f3a-a31c-4c14-810d-4f87e44f49bb" />

*Part of ko00010 Glycolysis / Gluconeogenesis, with made-up values for 32 KOs. Left: each box is filled by the coverage of its KOs. Right: the same fills, with a ring that shows a categorical status from a second column of the same file.*

<img width="3405" height="598" alt="2_glycolysis_sliced_rings" src="https://github.com/user-attachments/assets/6b9a30d3-a06e-4311-8de2-03203ff2be49" />

*Rings sliced by KO with `--reaction-border-slice-by accession`. Left: the fill is sliced by KO as well, so each segment of the ring adjacent to a fill slice is colored by the status of the KO. Right: the fill is drawn whole, reduced to a single value from KO values, while the ring is still sliced by KO, with segments proceeding clockwise from the top left corner. Each panel has its own fill key, since the left one shows single KOs and the right one shows the sum of each box.*

<img width="3515" height="1135" alt="3_carbon_metabolism_compound_rings" src="https://github.com/user-attachments/assets/f3e91d56-8714-487f-85f5-3ed6b82ed8df" />

*Part of ko01200 Carbon metabolism, with made-up coverages of 42 KOs and concentrations of 14 compounds. Left: a compound file with only a border column of values and no fill column of values fills its circles by presence, in pink, and these fills replace the colors that compounds take from touching reactions. Right: with `--compound-color none` indicating no fill, the circles keep the colors from the reactions, and the rings show the concentrations.*

<img width="3035" height="598" alt="4_glycolysis_rings_without_fills" src="https://github.com/user-attachments/assets/31e9ea03-e228-4128-baa0-02e8841ba025" />

*Left: a reaction file with only a border column fills its boxes by presence. Right: with `--reaction-color none`, the boxes show only their rings.*

## Features

- `--reaction-border-column` and `--compound-border-column` name the border value column to distinguish from a fill value column. The values are numbers by default, or categorical values with `--*-border-value-type categorical`. A row can leave its border cell empty.

- Rings are drawn on reaction boxes of standard maps and on compound circles of standard and overview maps. Global maps draw their circles without outlines, and lines take no rings. A thin black line separates the ring from the fill.

- Every option that reduces, summarizes, or colors the fill has a border version, such as `--reaction-border-colormap` and `--compound-border-sample-summary`. Some defaults differ. Border aggregations default to `mean` (`sum` for numerical fill`), numbers take `viridis` from 0.2 to 1 (`plasma_r` for numerical fill), and categorical values take Matplotlib's `Dark2` without its gray (`tab20`, rearranged and without grays, for categorical fill). The border summaries, such as `--reaction-border-sample-summary`, take an aggregation, such as `mean`, or a rule for categorical values. They refuse `count`, `count_continuous`, and `membership`, since the fill already shows presence across samples. They have no default, so the unified map of an input file with samples shows rings only where a border summary is given.

- Borders get keys of their own, such as `colorbar_reactions_border.pdf` and `colorbar_reactions_border_samples.pdf`. The colorbar label ends with `(border)`.

- `--reaction-border-slice-by accession` or `gene` divides each ring among the KOs or genes of its box. Where `--reaction-slice-by` names the same unit, the rings are aligned with the columns of the fill as bands. Otherwise each ring is divided on its own into up to 11 segments, sized by `--reaction-slice-weights` where a weight column is given. The slices of rings are listed in `slice_key_reactions_border.txt`. In a layer with a border column, the columns of a sliced box fit inside the ring, so a box holds up to 10 slices.

- `--reaction-color none` and `--compound-color none` leave the fills uncolored for an input file with a border column and no value column, so that the layer draws only its rings. On global and overview maps, compounds keep the fills they take from touching reactions in a reaction layer. Every option of the fill is refused with `none`, and so are the group options where no other layer uses them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7662a32d4fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.