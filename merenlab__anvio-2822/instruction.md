# Issue

**Title:** Add cyclic clocktime colormap available to `anvi-draw-kegg-pathways`

## Description

A cyclic colormap was needed to draw clock time (0 to 24 h) data in KEGG maps. The best named Matplotlib colormap for clock times is `twilight_shifted`, but does not work well for `anvi-draw-kegg-pathways`, as times close to noon are nearly white, making them hard to see against the white map background, and times close to midnight are nearly black, obscuring black box labels. This PR adds a colormap defined in anvi'o called `clocktime`, which has a similar layout as `twilight_shifted` with a yellow noon and lighter, purple midnight.

```bash
anvi-draw-kegg-pathways \
  --reaction-txt clock_time_data.txt \
  --reaction-category-colormap clocktime \
  --reaction-category-value-limits 0 24 \
  --draw-individual-files
```

In `clocktime`:
- 0 h and 24 h have the same color.
- Noon is yellow. The morning runs through blue, teal, and green. The afternoon and evening run through orange, rose, and plum. Midnight is purple.
- Lightness rises evenly to noon and falls evenly after it.
- Black text has a contrast of at least 3:1 on every color.

Limits of `0 24` should be used with clock time data, otherwise the scale will shift so that the purple color intended for midnight will correspond to the minimum and maximum element values rather than 0 h and 24 h, and the yellow color intended for noon will fall at the midpoint between the minimum and maximum values. Also to be avoided is colormap trimming with two extra numbers given to a colormap argument, such as `--compound-category-colormap clocktime 0.1 0.9`, as this breaks the color cycle at 0 h and 24 h.

With samples, the default `unified` summary shows which or how many samples contain an element. It does not make sense to use a quantitative function to aggregate element data in the `unified` summary — for example, the mean of clock data across two samples would combine an element at 23.9 h in one sample and 0.1 h in the other sample to the nonsense summary value of 12 h.

Consistent with Matplotlib colormaps, a reverse colormap is also available as `clocktime_r`. Every existing `anvi-draw-kegg-pathways` colormap option accepts `clocktime` or `clocktime_r`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0c1d507a9aa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.