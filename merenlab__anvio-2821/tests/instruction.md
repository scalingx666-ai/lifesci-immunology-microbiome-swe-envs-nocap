# Issue

**Title:** Change behavior of colorbar scale limits from conditional to fixed

## Description

In `anvi-draw-kegg-pathways`, `--reaction-value-limits`, `--compound-value-limits`, `--reaction-category-value-limits`, and `--compound-category-value-limits` set the limits of colorbar scales. They used to apply a limit only if some value crossed it. A limit that no value reached did not come into effect, so the colorbar neither started nor ended at it. Now a given limit always sets that end of the scale, with a value of `none` still setting the end of the scale from the data itself.

The colorbar now labels every given limit. A limit is marked `≤` or `≥` if values lie past it. For example, limits of `0 24` on values within a range of 0.6 to 23.7 now write labels at 0, 5, 10, 15, 20, and 24, while they used to write only 5, 10, 15, and 20.

This new behavior affects centering, which is now never permitted to move a limit. With two limits, the center has to be their midpoint; this also applies to the zero center that a normalization such as `relative_to_mean` supplies.

Among other related code changes and fixes, colorbar labels for values below 1e-8 no longer print as 0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `69ea808193e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.