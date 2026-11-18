# Issue

**Title:** Element normalization across samples/groups in anvi-draw-kegg-pathways

## Description

## Motivation

`anvi-draw-kegg-pathways` can color the reaction and compound elements of KEGG pathway maps by quantitative values provided in `kegg-reaction-txt` and `kegg-compound-txt` files. Values are given per KEGG Ortholog or Reaction accession and KEGG Compound accession. Map elements can represent multiple accessions, such as multiple KOs (enzymes) capable of catalyzing the same reaction. This becomes a problem in plotting the enrichment of an element in one sample (or group of samples) versus the others, e.g., a certain reaction element is 26% higher in one sample than the mean across all samples and 31% lower in another sample. The reason for this is that it is practically impossible for the user to input per-element values: elements are specific to each map, with their own IDs, associated with varying sets of accessions. Therefore, normalization of element values across samples should be carried out programmatically, with the user supplying the unnormalized values as before and a function mapping each to a normalized value.

## Usage

The new cross-sample/group element normalization arguments are `--reaction-element-normalization` and `--compound-element-normalization`. These take the name of a function and, optionally, a label for the rescaled colorbar.

```bash
anvi-draw-kegg-pathways \
  --reaction-txt kegg_reaction.txt \
  --reaction-element-normalization relative_to_mean \
  --draw-grid \
  -o OUTPUT_DIR --name-files --categorize-files
```

## Details

Certain functions have been built into anvi'o: `relative_to_mean`, `relative_to_median`, `difference_from_mean`, `difference_from_median`, `log2_ratio_to_mean`, `log2_ratio_to_median`, `z_score`, `rank`, `fraction_of_max`, and `fraction_of_total`. Instead of one of these values, the name of a pandas Series method that transforms each value to a new value — such as `abs` — can be provided.

The default colorbar label combines the value column header with the normalization, such as `abundance (z_score)`. A custom label can be provided as an optional second argument value to `--*-element-normalization`: remember to quote the value if it has spaces, such as `--compound-element-normalization relative_to_mean "concentration (change vs. mean)"`.

`--draw-individual-files` and/or `--draw-grid` are required with `--*-element-normalization`, as only the maps of individual samples or groups are rescaled, while the "unified" map summarizes unnormalized values. With `--groups-txt`, rescaling happens across groups, so `--*-sample-summary` has to pool each group's samples into a value for each element: left at its default, it counts by occurrence among the group's samples, which isn't something that should be rescaled.

A normalization whose neutral value is zero, such as `relative_to_mean` or `z_score`, centers the rescaled scale on zero and colors it with the diverging Matplotlib colormap, `RdYlGn`. Override these defaults with `--*-category-value-center` and `--*-category-colormap`, which control coloring of individual sample or group (category, rather than unified) maps.

An element that the normalization cannot value is left uncolored. A ratio, such as `relative_to_mean`, needs a positive value to measure against. A z-score can only be valued for an element found in more than one sample.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6d2092dae7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.