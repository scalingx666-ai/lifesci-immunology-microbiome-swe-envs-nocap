# Issue

**Title:** Pool map element instead of accession values in `anvi-draw-kegg-pathways` sample/group summaries

## Description

In `anvi-draw-kegg-pathways`, a value summary (`--reaction-sample-summary`, `--reaction-group-summary`, `--compound-sample-summary`, `--compound-group-summary`) counterintuitively pooled each accession across samples *before* the corresponding accession aggregation (`--reaction-accession-aggregation`, `--compound-accession-aggregation`) combined the accessions of a map element. A map element on the `unified` map therefore did not summarize what was drawn on the elements of the individual sample maps.

For example, one element on map 00010 stands for K00174 and K00175. In Samples 1 and 2, the element was represented by data for K00174 but not K00175 and drawn with respective values of 27 and 4.5. In Sample 3, the element was represented by data for K00175 but not K00174 and drawn with a value of 23.5. With `--reaction-sample-summary mean` and `--reaction-accession-aggregation sum`, first the mean of each accession was taken — for K00174, (27 + 4.5) / 2 = 15.75, and for K00175, 23.5 / 1 = 23.5 — and then the accessions were summed — 15.75 + 23.5 = 39.25, a value for the element higher than in any of the three samples. In contrast, the expected order of operations first sums the accession values for the element in each sample — in each sample, the element is represented by only one KO, so the three sample values after summing are still 27, 4.5, and 23.5 — and then the element values averaged — (27 + 4.5 + 23.5) / 3 = 18.3. This bad order of operations could also result in a `std` summary showing a spread despite every sample map drawing the same value.

This PR contains the fix so that summaries now pool the values of map elements. Without groups, the sample summary pools element values on the `unified` map. With groups, each group's map summarizes its own samples, and the group summary pools the groups on the `unified` map. The fix does not affect presence summaries and element normalization, which already worked properly, element by element.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e82967f2691`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.