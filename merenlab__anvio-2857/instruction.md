# Issue

**Title:** Speed up `anvi-draw-kegg-pathways` and show per-map progress

## Description

This PR makes `anvi-draw-kegg-pathways` faster and its progress bars more informative.

## Blank grid panels

A map grid panel can contain a blank map that does not have any map elements with data. A blank map for the pathway is now drawn once and copied to every panel that needs it, instead of being drawn again for each panel. Blank maps are no longer drawn for samples not included in the grid, which were deleted unused.

## `rl_accel` dependency

This is a C accelerator for `reportlab`, which otherwise encodes each map's base image in pure Python, taking ~40% of the time to draw a standard or overview map. `rl_accel` is now included in `pyproject.toml`.

Timings with 6 samples and 46 grids, where 5 samples lack most maps:

|                                 | Before | Blank maps drawn once | With `rl_accel` |
|-------------------|--------|-----------------------|------------------|
| Blank maps drawn | 206    | 42                                   | 42                         |
| Grid stage              | 35.8 s | 8.4 s                               | 5.3 s                     |
| Whole run              | 60.0 s | 33.5 s                             | 20.6 s                   |

## Progress bars

The progress bar for maps of each sample, contigs database, genome, or group now shows the pathway being drawn. Before, it showed "..." throughout. The map grid bar now also shows each pathway that gets a blank map.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53aa59a19719`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.