# Issue

**Title:** Scale barplot thicknesses relative to tree size; makes default layout barplot lengths look thicker; fix a small Colorer bug

## Description

Part of the work on #276. This should make barplots look more consistent between the rectangular and circular layouts, and in particular make circular layout barplots' defaults look a lot more legible. Barplot lengths, rather than being in arbitrary units, are now scaled by the tree "thickness" (root to farthest tip width in the rectangular layout, 2 * that distance for the circular layout).

Old:
![old](https://user-images.githubusercontent.com/4177727/98457023-4ede2a80-2138-11eb-8294-d213d72aee59.gif)

New:
![new](https://user-images.githubusercontent.com/4177727/98457025-50a7ee00-2138-11eb-8a45-54dae6e0a4f8.gif)

Note 1: currently I have this set so that the default barplot layer length, 100, is equal to 1/10th of the tree "thickness." If folks would prefer a thinner default setting, we can adjust the scaling code as needed.

Note 2: I also noticed and fixed a small problem with the Colorer module, where the "freebie" problems with barplot borders we discussed in #400 re-emerged. Basically, this was because `rgbToFloat()` was being called on a GL array (with colors in the range [0, 1]), not on an RGB array (with colors in the range [0, 255]) -- so the RGB float colors didn't match. I added and tested some code to do the RGB -> GL conversion. I also bit the bullet and added a test that verifies that the "freebie" checking works (i.e. unnecessary triangles aren't being drawn), and added some extra barplot testing code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13438f9646b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.