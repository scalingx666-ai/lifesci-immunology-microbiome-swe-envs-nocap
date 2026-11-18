# Issue

**Title:** Add `anvi-draw-kegg-pathways` angular deviation summary of values that repeat after a period

## Description

In `anvi-draw-kegg-pathways`, `--reaction-value-period` and `--compound-value-period` allows the `unified` map to draw the circular mean of each element's values in the samples (#2831, #2832). It is also valuable to be able to show how much samples disagree; the circular mean does not distinguish between samples 11 h apart and samples at the same time.

This PR adds `angular_deviation`, the circular counterpart of `std`. It colors each element on the `unified` map by how far its values in the samples or groups are spread apart. For a period of 24, it runs from 0 h, where every sample has the same time, to 5.4 h, where the times cancel out. For times close together, it is close to their standard deviation.

```bash
anvi-draw-kegg-pathways --reaction-txt clock_time_data.txt \
                        --reaction-value-period 24 \
                        --reaction-sample-summary angular_deviation \
                        --draw-individual-files \
                        -o output_dir
```

`angular_deviation` requires a period, but a spread is a plain number, not a point in the period, so:
- Only the summary that colors the `unified` map (`--reaction-sample-summary` without groups and `--reaction-group-summary` with groups) takes `angular_deviation`. It is refused as a gene or accession aggregation, and as the sample summary of a grouped run.
- An element needs values from at least 3 samples or groups. The spread of two values is only the gap between them. Elements with one or two values are left uncolored.
- The `unified` scale runs from 0 to the largest spread there can be, so limits and centers on it are refused. Its colorbar is labeled `<value column> angular deviation`.
- The `unified` map uses the sequential `plasma_r`, unless `--reaction-colormap` names another colormap. A cyclic colormap is refused there. The maps of the individual samples still show each sample's times in `clocktime`.
- On global and overview maps, compound colors on the `unified` map are averaged as plain numbers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6510ea602baa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.