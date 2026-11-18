# Issue

**Title:** Circular averaging of compound colors from reactions on global/overview maps

## Description

On global and overview maps drawn from reactions alone, `anvi-draw-kegg-pathways` colors each compound circle by the average value of the reaction lines that touch it. With the cyclic `clocktime` colormap, this average made no sense. Lines at 23.9 h and 0.1 h gave the compound the color of 12 h.

With `clocktime` or `clocktime_r`, these values are now averaged on a circle. 23.9 h and 0.1 h give 0 h, and 22, 23, and 1 h give 23.3 h. Some times have no average on a circle, such as 6 h and 18 h. Those compounds take the plain average, as before. Compounds touched by a single line are unchanged. Other colormaps still use the plain average. That includes a trimmed `clocktime`, since trimming breaks the color cycle.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `412befd98661`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.