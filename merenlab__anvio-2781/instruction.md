# Issue

**Title:** Enable coloring by quantitative input, coloring of compound circles, and custom category colors

## Description

## Summary

This PR introduces `kegg-reaction-txt` and `kegg-compound-txt` input files for `anvi-draw-kegg-pathways`, enabling coloring by quantitative continuous variables and coloring of compound circles on KEGG maps.

These tab-delimited text files are alternatives to the existing input types: one or more contigs databases, a pan database, or a metabolic model json file.

`kegg-reaction-txt` (`--reaction-txt`) controls the "reaction layer" of reaction lines and boxes. `kegg-compound-txt` (`--compound-txt`) controls the "compound layer" of compound circles. Reactions and compounds can be colored simultaneously using both files, so that maps can, for example, display transcript levels alongside metabolite concentrations.

## Map element text file format

The formats of these files are documented in their artifacts.

`kegg-reaction-txt` contains
- a mandatory `accession` column of KO IDs (`K#####`) or KEGG reaction IDs (`R#####`) (all one type of ID or the other)
- a `gene_id` column (optional)
- a `sample` column (optional)
- a single auto-detected numeric column of any name besides the three just given (optional)

`kegg-compound-txt` contains
- a mandatory `accession` column of KEGG compound IDs (`C#####`)
- a `sample` column (optional)
- a single auto-detected numeric column of any name besides the two just given (optional)

Without the numeric column, layers are colored by presence/absence as the program currently does; with samples and groups (`groups-txt`), presence is colored qualitatively by **membership** for ≤ 3 categories and quantitatively by **count** for > 3 categories. This allows one layer to be colored by presence and the other by numerical values, such as the compound layer colored by quantitative metabolomics and the reaction layer colored by occurrence of a KO in a genome.

## Numerical value reduction

Values from the numerical column are reduced by four options, each addressing a separate issue:
- `--reaction-gene-aggregation` combines the genes carrying an accession from the `gene_id` column, and is `sum` by default; for example, sum the mass spectral abundances of the same KO encoded by different ORFs
- `--reaction-accession-aggregation`/`--compound-accession-aggregation` combines the accession constituents of each map element (~23% of reaction elements are associated with multiple KOs, and ~2% of compound elements with multiple KEGG compounds), and is `sum` by default
- `--reaction-sample-summary`/`--compound-sample-summary` reduces a set of samples in the **unified** map, and can display presence/absence of elements across samples (`membership` or `count`), or can aggregate across samples with a `pandas` aggregation function name (`sum`, `mean`, `std`, ...)
- `--reaction-group-summary`/`--compound-group-summary` reduces a set of sample groups in the **unified** map; as with the sample summary, displaying presence/absence of elements across groups (`membership` or `count`), or can aggregate across groups with a `pandas` function

The last two sets of options for sample and group summaries affect **unified** maps that consolidate data from multiple samples or groups of samples into a single map; unified maps are always produced when samples and groups are provided. By default, sample and group summaries are colored by presence; numeric value aggregation makes sense for commensurable categories, such as the mean value of replicate experiments, but not for different genomes or samples from different environments.

`--draw-individual-files` and `--draw-grid` with samples produce a unified map comparing all samples plus per-sample maps which default to the numeric data provided in the input text files, or presence without a numeric column. With groups, `--draw-individual-files` and `--draw-grid` produce a unified map comparing all groups plus per-group maps which default to presence coloring by `count`, regardless of whether a numeric column is given.

To understand the group defaults, consider two groups of marine metagenomes from the Pacific and Atlantic Oceans, with 5 samples in the former and 3 samples in the latter. The unified map of groups are colored by membership, since there are only 2 groups (≤ 3): one color for reactions present in the Pacific, one color for reactions present in the Atlantic, and one color for reactions present in both basins. ("Presence" in a group is defined by `--group-threshold`, here the proportion of samples in a group containing a reaction for it to be colored as present in the group.) Per-group maps are colored by `count` of samples, despite there being ≤ 3 samples in the Atlantic group; the Pacific map has a colorbar spanning 0 to 5 samples, and the Atlantic 0 to 3 samples. Aggregation by `mean` of sample numeric values in the group maps could make sense for replicate samples, but is not generally applicable like the sample count, as mentioned above.

## Custom category colors

`kegg-category-colors-txt` files can be provided to set category colors in lieu of a colormap. The format of this file is documented in its artifact.

`kegg-category-colors-txt` contains
- a mandatory column, with any header, containing categories and combinations of categories
- a mandatory `color` column of RGB hex codes per category, e.g., #7d5ba6

If coloring by sample — or contigs database or pan genome — membership, then each value in the first column should be a sample or database project or genome name, or a combination of names to set the color of elements found in multiple samples or databases or genomes. For example, the file can have separate rows for Sample A, Sample B, and "Sample A, Sample B". Note that a comma delimiter is used to denote combinations — as seen in colorbar labels — and so commas cannot be found in category names. Groups are treated the same way, with categories being the names of groups from the `groups-txt` file and combinations of groups also allowed. For category combinations *not* specified in `kegg-category-colors-txt`, the colors of the individual categories are blended together. The file can contain the names of inapplicable categories that are not being mapped so that the same file can be reused to map different sets of categories.

Reactions and compounds can use the same or different sets of custom colors: `--reaction-category-colors` and `--compound-category-colors` can point to the same or different `kegg-category-colors-txt` files.

## Examples

### KO numerical values

Here is the head of a `kegg-reaction-txt` file containing KO accessions associated with values of a metric called "complexity_normalized."

| accession | complexity_normalized |
| --- | --- |
| K00003 | 0.0 |
| K00007 | 0.0689655172413793 |
| K00010 | 0.0 |
| K00012 | 0.01149425287356322 |
| K00013 | 0.0 |
| K00014 | 0.0 |
| K00020 | 0.03553566728086338 |
| K00024 | 0.0 |
| K00029 | 0.0 |
| K00031 | 0.0 |
| ... | ... |

The following command draws all of the maps in which KOs occur — including maps that only contain KOs with a numerical value of 0.0.

```bash
anvi-draw-kegg-pathways --reaction-txt kegg_reaction-complexity_normalized.txt -o OUTPUT_DIR --name-files --categorize-files
```

A single colorbar file is produced, `colorbar_reactions.pdf`; this is shared across all maps.

<img width="142" height="412" alt="Screenshot 2026-08-12 at 7 52 20 AM" src="https://github.com/user-attachments/assets/d5c1f3bd-54ae-4597-a851-ab57db7f7533" />

The global metabolism map written to `OUTPUT_DIR/unified/Metabolism/Global_and_overview_maps/kos_01100_Metabolic_pathways.pdf` colors the KOs from the input file, including those with a value of 0.0.

<img width="1341" height="868" alt="Screenshot 2026-08-12 at 7 56 06 AM" src="https://github.com/user-attachments/assets/80181b72-dd3b-4d92-9936-95c70cf08f36" />

This map clearly shows that KOs with positive values of the metric are concentrated in certain pathways, which can be identified by zooming in on the global map.

Perusal of the output maps reveals that most variation in the metric occurs among KOs involved in the biosynthesis of O-antigen nucleotide sugars, as seen in the overview map, `kos_01250_Biosynthesis_of_nucleotide_sugars.pdf`, and the standard pathway map, `kos_00541_Biosynthesis_of_various_nucleotide_sugars.pdf`.

<img width="891" height="975" alt="Screenshot 2026-08-12 at 7 58 31 AM" src="https://github.com/user-attachments/assets/ad634a22-69f0-406a-b7cd-05ee33c172fb" />

<img width="582" height="953" alt="Screenshot 2026-08-12 at 8 01 50 AM" src="https://github.com/user-attachments/assets/15c20a93-8820-4197-a01b-80eb24a31460" />

### Compounds and reactions

The paper, ["An atlas of metabolites driving chemotaxis in prokaryotes"](https://www.nature.com/articles/s41467-025-56410-y), compiled data on all of the studies that could be found measuring the chemotactic response of prokaryotes to added compounds. Here, maps were produced that show which compounds were tested in the context of pathways from the organisms.

Here is the head of the `kegg-reaction-txt` file containing KOs associated with genes and samples — organisms identified by GenBank genome accession (rows are sorted by genome and then gene ID).

| gene_id | accession | sample |
| --- | --- | --- |
| 1 | K01626 | GCA_000015545 |
| 2 | K21084 | GCA_000015545 |
| 3 | K20329 | GCA_000015545 |
| 4 | K07795 | GCA_000015545 |
| 5 | K12976 | GCA_000015545 |
| 6 | K06006 | GCA_000015545 |
| 7 | K03554 | GCA_000015545 |
| 8 | K11103 | GCA_000015545 |
| 9 | K20975 | GCA_000015545 |
| 9 | K10819 | GCA_000015545 |
| ... | ... | ... |

Here is the head of the `kegg-compound-txt` file containing KEGG compounds and samples — organisms identified by GenBank genome accession.

| accession | sample |
| --- | --- |
| C00002 | GCF_000008865 |
| C00002 | GCF_000196175 |
| C00002 | GCF_000006765 |
| C00007 | GCF_000008865 |
| C00007 | GCA_054657015 |
| C00007 | GCF_002995515 |
| C00007 | GCF_000829825 |
| C00007 | GCA_902725215 |
| C00007 | GCA_900093605 |
| C00007 | GCA_036689815 |
| ... | ... |

The following command draws all of the maps containing the reactions or compounds, coloring by count of genomes containing the KO or in which the compound was tested.

```bash
anvi-draw-kegg-pathways --reaction-txt kegg_reaction.txt --compound-txt kegg_compound_tested_organisms.tsv --compound-colormap YlGnBu 0.2 1.0 -o OUTPUT_DIR --name-files --categorize-files
```

Since the number of samples (genomes) is so great, colorbars are automatically formatted to be continuous rather than have discrete bands; here is `colorbar_reactions.pdf`.

<img width="156" height="448" alt="Screenshot 2026-08-12 at 8 35 23 AM" src="https://github.com/user-attachments/assets/76fcbf6d-207d-492d-8453-ae0e1bd5f829" />

A different colormap than the default was used for compounds to distinguish them from reactions in a cooler spectrum; here is `colorbar_compounds.pdf`.

<img width="159" height="453" alt="Screenshot 2026-08-12 at 8 36 11 AM" src="https://github.com/user-attachments/assets/3d0cd707-f2cd-4029-925c-955f7969af56" />

The overview map of carbon metabolism written to `OUTPUT_DIR/unified/Metabolism/Global_and_overview_maps/kos_01200_Carbon_metabolism.pdf` shows numerous compounds that have been tested, with certain intermediates of the citric acid cycle, particularly malate, being especially well-studied.

<img width="894" height="959" alt="Screenshot 2026-08-12 at 8 39 20 AM" src="https://github.com/user-attachments/assets/5cb3db2e-e0f1-4aeb-a805-52116f7025b2" />

The ABC transporter chart, `kos_02010_ABC_transporters.pdf`, highlights common types of transporters among the genomes — the substrates of which might also be common attractants — and thus where gaps might exist in studies demonstrating a chemotactic response.

<img width="692" height="988" alt="Screenshot 2026-08-12 at 8 43 22 AM" src="https://github.com/user-attachments/assets/37c994ab-e33b-4016-9273-29451d2a604e" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `acde23486ef1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.