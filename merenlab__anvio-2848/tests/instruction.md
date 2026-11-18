# Issue

**Title:** Add `anvi-draw-kegg-pathways` `difference_from_circular_mean` element normalization for values that repeat after a period

## Description

`anvi-draw-kegg-pathways` refused `--reaction-value-period` with `--reaction-element-normalization`, because the existing normalizations compared values on a line rather than on a circle. For clock times, the linear `difference_from_mean` gets offsets wrong across midnight — 23 h and 1 h are 22 h apart on a line and 2 h apart on a clock.

This PR adds a normalization across samples for periodic data, `difference_from_circular_mean`. On each sample's map, each element shows its offset from the element's circular mean across the samples. With a period of 24, offsets run from -12 to 12 h, and -12 and 12 are the same time. A sample that peaks 3 h after the average time is shown as +3 h. With groups, each group's circular mean is compared with the circular mean of the groups.

```bash
anvi-draw-kegg-pathways --reaction-txt clock_time_data.txt \
                        --reaction-value-period 24 \
                        --reaction-element-normalization difference_from_circular_mean \
                        --draw-individual-files \
                        -o output_dir
```

**Features:**
- A period is required; `difference_from_circular_mean` is the only normalization accepted with a period.
- The scale is fixed from -P/2 to P/2, with a tick at 0. Limits of exactly `-12 12` are accepted. Other limits and centers are refused.
- The scale uses the `clocktime` colormap unless `--reaction-category-colormap` names another colormap. With 0 at its middle, `clocktime` is lightest at 0 and darkest at ±12. Its lightness is symmetric about 0. Earlier offsets take morning colors and later ones take afternoon colors.
- The colorbar is labeled `<value column> - circular mean`.
- An element found in one sample gets 0, as with `difference_from_mean`.
- An element whose values cancel out, such as 6 h and 18 h, has no circular mean. It is left uncolored on every individual map, and a warning names it.
- On global and overview maps drawn from reactions alone, each compound takes its color from the reaction lines that touch it. These colors are averaged on a circle. Lines at +11.5 h and -11.5 h then give the compound the color of ±12 h, not of 0 h. This works because the scale runs from -12 to 12, exactly one period, so its two ends are the same time.
- The `unified` map is not normalized.

Messages that suggest a summary such as `'mean'` now suggest `'circular_mean'` when there is a period. Runs without the normalization are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `572ad6cf63d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.