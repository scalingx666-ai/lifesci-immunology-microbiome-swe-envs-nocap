# Issue

**Title:** Limit, center, and separately color `anvi-draw-kegg-pathways` value scales

## Description

A continuous color scale drawn from a `kegg-reaction-txt` or `kegg-compound-txt` value column currently spans exactly the values it is given, in one colormap shared by every map in the run. This branch adds three ways to shape that in the unified and per-sample/per-group maps' reaction and compound layers.

| Operation | Unified reaction layer | Unified compound layer | Sample/group reaction layer | Sample/group compound layer |
|---|---|---|---|---|
| Bound a scale | `--reaction-value-limits` |  `--compound-value-limits` | `--reaction-category-value-limits` | `--compound-category-value-limits` |
| Center a scale | `--reaction-value-center` | `--compound-value-center` | `--reaction-category-value-center` | `--compound-category-value-center` |
| Separately color sample/group scales | `--reaction-colormap` | `--compound-colormap` | `--reaction-category-colormap` | `--compound-category-colormap` |

- **Limits** take a minimum and a maximum, either of which may be `none`. A limit only truncates where the values actually cross it. A truncated end of the colorbar is marked `≥` or `≤`.

- **Centering** takes a bare flag (center on 0) or a number. The scale is widened, never narrowed: it comes to span the same distance either side of the center, so the neutral color of a diverging colormap stands for the centered value however lopsided the data are. The colorbar is ticked at the center.

- **Category colormaps** let the per-sample/per-group scale be colored differently than the `unified` map's scale, for when the two show different kinds of quantities. For example, `--reaction-sample-summary std` shows spread — all positive values — on `unified` maps and underlying values — perhaps including negative values — on per-sample/per-group maps. Regardless of whether different colormaps are provided, each scale writes its own colorbar file.

Database, pangenome and reaction-network-JSON inputs reject `--*-value-limits`, `--*compound-value-center`, and `--*-category-colormap`, their scales counting sources rather than taking a quantitative input, exclusive to `--kegg-*-txt` input.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `489932826aaa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.