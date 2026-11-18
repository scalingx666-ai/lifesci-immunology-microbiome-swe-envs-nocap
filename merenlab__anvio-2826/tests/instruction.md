# Issue

**Title:** speed up `anvi-draw-kegg-pathways` reserved-color check for runs with many samples

## Description

`anvi-draw-kegg-pathways` checks that no layer color matches a color that the pathway maps reserve for unhighlighted elements, such as white for reaction boxes or compound circles and black for reaction arrows. The check finds the colors a layer will draw by sampling its colormap at every value collected from the maps.

With a sample column, there is a value for every element in every sample. Runs with hundreds of samples collect millions of values. The check colored them one at a time, so it could take minutes.

The check now colors all of a scale's values at once and converts each distinct color only once. The scale shared by the maps of individual samples or groups is now checked only when one of those maps is drawn. In a run with 300 samples, the check went from about 150 s to under 3 s, or to almost nothing when only the 'unified' map is drawn.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2f22cef12cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.