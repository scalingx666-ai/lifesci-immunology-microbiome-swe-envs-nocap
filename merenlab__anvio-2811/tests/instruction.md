# Issue

**Title:** Add `--skip-unified-maps` flag to `anvi-draw-kegg-pathways`

## Description

The requirement that `anvi-draw-kegg-pathways` always produce a 'unified' map is too rigid and can sometimes be inappropriate given the data. A 'unified' map summarizes samples and groups — genomes of a pangenome, contigs databases, samples in an input text file, or groups of samples. It is also the map produced when data comes from a single source, such as a single contigs database, a metabolic model JSON file, an input text file without a 'sample' column. A single source has no sample dimension, so its one map takes the 'unified' scale, and the options shaping that scale are what color it.

Summarizing is not always meaningful. Without a summary option, presence across sources is colored by which sources contain an element with three or fewer of them, and by the count of sources containing an element above that. Coloring by presence can be irrelevant or misleading when the sources are incommensurable, coming from different places, times, or conditions.

A new flag, `--skip-unified-maps`, leaves that map out. The `unified` output subdirectory is not written. The colorbars keying 'unified' maps, `colorbar_reactions.pdf` and `colorbar_compounds.pdf`, are not written either — the exception is a reaction or compound layer with no color scale of its own for the individual maps, so the shared scale shown in a 'unified' colorbar is the only key to their colors. Map grids no longer lead with the summary panel labeled `all`, and hold only panels for individual sources or groups.

The flag needs individual maps to draw, so `--draw-individual-files` and/or `--draw-grid` is required with it.

With `--skip-unified-maps`, `--groups-txt` may now be given without `--group-threshold`, since only the 'unified' map uses the threshold — a group's own map counts that group's own sources, with no regard to the threshold.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6a5e83f56a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.