# Issue

**Title:** Add circular mean for values that repeat after a period in `anvi-draw-kegg-pathways`

## Description

`anvi-draw-kegg-pathways` reduced every value on a line, which breaks values that repeat, such as clock times. The default accession aggregation `sum` added the times of the KOs on one map element. For example, 16 h and 19.5 h gave 35.5 h. With limits of `0 24` this was drawn in the color of midnight. `mean` was no better, since the mean of 23.5 h and 0.5 h is 12 h.

This PR adds `--reaction-value-period` and `--compound-value-period`. They give the period after which a layer's values repeat, such as 24 for clock times in hours. Each reduction of the values then takes their circular mean, `circular_mean`. The circular mean of 23.5 h and 0.5 h is 0 h, and that of 22 h, 23 h and 1 h is 23.3 h.

```bash
anvi-draw-kegg-pathways --reaction-txt clock_time_data.txt \
                        --reaction-value-period 24 \
                        --reaction-sample-summary circular_mean \
                        --reaction-colormap clocktime \
                        --reaction-value-limits 0 24 \
                        --reaction-category-value-limits 0 24 \
                        --draw-individual-files \
                        -o output_dir
```

**With a period:**
- `circular_mean` is the default of `--reaction-gene-aggregation` and `--reaction-accession-aggregation`, in place of `sum`.
- `circular_mean` is the only name that the aggregation options and the sample and group summaries accept. Presence summaries still work.
- An element normalization is refused, since every normalization compares values on a line.
- Values that cancel out, such as 6 h and 18 h, have no circular mean. Such an element is left uncolored, and a warning says so.

**Refused inputs:**
- `circular_mean` without a period.
- A period that is not a positive number.
- A period for a file with no value column.
- A period for a database or pangenome input.

Runs without a period are unchanged. The period does not change the color scales, so clock times still need limits of 0 24.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09fb97b764e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.