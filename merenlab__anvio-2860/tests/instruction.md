# Issue

**Title:** Draw reaction elements in slices by accession or gene in `anvi-draw-kegg-pathways`

## Description

A reaction box or line on a KEGG map often stands for several KOs or KEGG reactions, and their values are reduced to one color, which can obscure differences in the underlying accessions and genes. This PR adds `--reaction-slice-by`, which draws element slices instead. Each slice is one accession or one gene and takes the color of its own value, so the map shows where the KOs or genes of an element differ.

```bash
anvi-draw-kegg-pathways --reaction-txt kegg-reaction.txt \
  --reaction-slice-by accession \
  --draw-individual-files \
  -o output_dir
```

<img width="2566" height="905" alt="1_glycolysis_whole_vs_sliced" src="https://github.com/user-attachments/assets/91bb2abc-de51-4ba1-bacb-33682665238d" />

*Part of ko00010 Glycolysis / Gluconeogenesis, with made-up values for 30 KOs. Left: each box shows the mean of its KOs. Right: each KO with a value gets its own slice. It should be evident how the KO colors on the right average to the colors on the left.*

<img width="2566" height="905" alt="2_glycolysis_equal_vs_weighted" src="https://github.com/user-attachments/assets/03e912fb-9446-41a8-8de8-a03e94e621df" />

*The same region with equal slices, and with slices sized by a column of weights. For example, the color could represent the size exclusion chromatographic retention time of a protein, and the weight its mass spectral intensity — if two proteins carry out the same reaction, but they have different sizes and thus retention times, then a box will be divided into slices with two colors for the sizes, and the more abundant protein will take the bigger share of the box.*

<img width="2566" height="961" alt="3_glycolysis_categorical" src="https://github.com/user-attachments/assets/ba3f7eff-9148-48b0-a354-4ebb185aa276" />

*Categorical values. Left: a rule, such as a plurality of KOs having the same categorical value, chooses one value per box. Right: every value is shown.*

<img width="2618" height="1281" alt="4_global_map_lines" src="https://github.com/user-attachments/assets/f3e2eec5-53ec-401b-bd6c-c6590cf1d581" />

*Part of ko01100 Global metabolism. Sliced lines are drawn as repeating dashes, fitted to the part of each line that compound circles leave visible.*

<img width="2618" height="1281" alt="5_global_map_weighted_lines" src="https://github.com/user-attachments/assets/02648532-8653-4f5f-8246-b81741d3900c" />

*The same part of ko01100, with equal dashes and with dashes sized by a column of weights. Where a share is small, a line holds fewer cycles of dashes, so that the shortest dash stays visible. A compound circle takes its color from the share-weighted mean of the slices of a line that touches it, so some circles change too.*

## Features

- `accession` slices a KO file by KO and a reaction file by KEGG reaction. `gene` slices by the `gene_id` column, which can name anything that carries the annotation, such as a gene, transcript, protein, or gene cluster. A gene with rows for several KOs of one element is one slice, whose value is the mean of those rows by default.

- Maps that show values are sliced. Maps that show presence are drawn whole. Only accessions or genes with a value on a map get a slice there, in the order of the KGML file.

- Slices are equal by default. `--reaction-slice-weights` names a column of weights that sets their shares. `--reaction-slice-share-summary` sets how shares are pooled on the map of a group and on the 'unified' map. There are two summary rules:
  - `share_mean`, the default, finds the share of each slice in each sample and averages these shares. Each sample counts once, so the weights need to be comparable only within a sample.
  - `pooled_sum` adds up the weights of each slice over the samples and divides each sum by the total of the element. A sample with more weight counts for more, so the weights should be in the same units in every sample, such as counts at comparable sequencing depth.

  For example, the KOs, K1 and K2, of one element weigh 90 and 10 in S1, 1 and 9 in S2, and 5 and nothing in S3. On the 'unified' map, `share_mean` gives K1 (0.90 + 0.10 + 1.00) / 3 = 0.67 of the element. `pooled_sum` gives it 96 / 115 = 0.83, since S1 has most of the weight.

- An element with too many slices to draw is drawn whole, in the color of the share-weighted mean of its slice values, or of the value a rule chooses for categorical layers. This happens where an equal slice would be narrower than 8 points in a box, or shorter than the line is wide.

- `slice_key_reactions.txt` says what each slice stands for (new artifact `kegg-slice-key-txt`). Slices are too narrow to label, and a box label names only the first KO of the element. One file covers every map of the run, at the top of the output directory. It has a row for each slice on each drawn map, with the KEGG map, the drawn map (`unified`, a sample, or a group), the KGML entry and its coordinates, and the slice's position, accession, gene, value, share, and color. An element drawn whole has a row for each slice it would have had, with the reason.

## Other: fixes to reading `kegg-reaction-txt` and `kegg-compound-txt` files

- Pandas renamed a repeated column, so a second `coverage` column was read as `coverage.1`. With `--reaction-slice-weights coverage`, the weights came from the first column and the values silently came from the second. A second `sample` column could become the value column in the same way. A repeated name is now refused.

- A value column named `__accession` was overwritten by the column of the same name that anvi'o adds. A name that starts with `__` is now refused.

- Numeric and presence files took a double quote to start a quoted field. A stray quote crashed the reader or merged the rows up to the next quote into one field, so a presence file could silently lose accessions. A stray quote in a header crashed the run, even for a categorical file. Every file is now read with quotes kept as text, as categorical files already were. A pair of quotes around a whole field, as R writes it, is still dropped, and a number that holds any other quote is refused.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a1a6ec3c81c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.