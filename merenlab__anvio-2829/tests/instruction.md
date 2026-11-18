# Issue

**Title:** Make `anvi-draw-kegg-pathways` presence layer maps independent of the row order of the input

## Description

A map keeps one drawing priority per color. When several entries are given one color, the last one sets its priority. Presence layers color entries in the order of their input: the rows of a text file, or the database order. Two counts can share a color. This happens on a continuous count scale, with a cyclic or repeating colormap, or with discrete group bands asked for outright. Changing only the row order of the input could then change the drawing order and the derived compound colors. For example, 6 samples with `--reaction-sample-summary count_continuous --reaction-colormap clocktime` gave 802,893 different pixels on 01100 between shuffled and sorted rows.

This PR adds a layer spec key, `keep_highest_priority`. The two presence specs set it. `_stage_element_color` then gives each color the highest priority among the entries given that color on the map. Maps where only one count uses a shared color are unchanged. Quantitative layers are unchanged. Their order comes from a groupby, which does not depend on row order. The `_membership_colorer` docstring wrongly said that a shared color keeps each count's own priority — this is corrected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03222e7fff3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.