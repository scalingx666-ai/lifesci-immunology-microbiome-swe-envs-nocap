# Issue

**Title:** Set `anvi-draw-kegg-pathways` color scales, default colormap, and compound averaging for values with a period

## Description

`anvi-draw-kegg-pathways` `--reaction-value-period` and `--compound-value-period` (#2831) changed only how values are reduced: genes to KEGG accessions, accessions to map elements, and map elements across samples and groups. They did not change how the values are colored. Each color scale still spanned the values it was given, and the default colormap was still `plasma_r`. So clock times also needed a cyclic colormap and limits of `0 24` on each scale. Otherwise the colors would not mean the same hours.

Now, with a period:
- Each color scale of values runs from 0 to the period. Limits of exactly `0` and the period are accepted. Other limits are refused, and so are centers.
- Without a colormap, the scales use the cyclic `clocktime`.
- On global and overview maps drawn from reactions alone, compound colors are averaged on a circle, whatever the colormap. Without a period, `clocktime` still averages them on a circle, as before.

```bash
anvi-draw-kegg-pathways --reaction-txt clock_time_data.txt \
                        --reaction-value-period 24 \
                        --reaction-sample-summary circular_mean \
                        --draw-individual-files \
                        -o output_dir
```

Before this PR, the same run also needed `--reaction-colormap clocktime`, `--reaction-value-limits 0 24`, and `--reaction-category-value-limits 0 24`. The period now sets all three. Each scale runs from 0 to 24 h and is colored by `clocktime`.

Without `--reaction-sample-summary`, the `unified` map summarizes presence. It shows which samples, or how many samples, contain each element. `--reaction-sample-summary circular_mean` replaces this presence summary with a summary of the values. Each element on the `unified` map then shows the circular mean of its times in the samples that have a value for it. The maps of the individual samples still show each sample's own times.

So before this PR, the same run needed this:

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

Runs without a period are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ee1cc886a33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.