# Issue

**Title:** Color derived compound circles only from the reaction lines that touch them

## Description

On global and overview maps, compound circles take their colors from reactions when only the reaction layer is drawn. Until now, `kgml.Pathway.color_associated_compounds` routed each reaction's vote by name: it found the reaction's Reaction element by its name, then gave the vote to every circle of each compound that element names, anywhere on the map. A compound was therefore colored wherever it occurred on the map, including in other places where it did not participate in the reaction and was only touched by gray lines. Additionally, two different Reaction elements can share a name, which caused some lines to vote through another line's Reaction element, leaving their own circles uncolored. Some circles are also reached through several KGML elements, which each received its own list of votes. Only the first list colored it, so a circle's color could depend on the order of elements in the KGML file.

This PR solves these problems by assigning votes to circles, not compounds:

- On global and overview maps, a line votes for the circle nearest each of its ends, if the circle's edge lies within 2 points (global, 1x KGML) or 48 points (overview, 2x KGML, where arrows stop short of circles).
- On other maps, an entry votes for the compound entries named by the Substrate and Product IDs of the Reaction element with the entry's own ID. Only API callers reach this branch, because `anvi-draw-kegg-pathways` imparts compound colors from reactions only on global and overview maps.
- Each circle pools the votes of the lines that touch it, once each, and a transfer function is called once per circle.

Effects on drawn maps:

- Stray circles disappear. Coloring one reaction at a time, they drop from 387, 44, and 151 on 01100, 01110, and 01120 to 0.
- Under `--original-color`, the set of colored circles now equals the set KEGG colors on all three global maps.
- Lines without a Reaction element of their own in the KGML file now color the circles they end on. This colors, for example, the H+ circles of oxidative phosphorylation and Glucono-1,5-lactone on 01200.
- A compound drawn several times is no longer colored as a set: each circle takes only the votes of the lines that touch it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a8652e6dee9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.