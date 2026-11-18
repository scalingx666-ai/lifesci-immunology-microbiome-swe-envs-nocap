# Issue

**Title:** Tile Graphviz layouts in a nice way

## Description

Current algorithm arranges components from top to bottom, left to right, going from biggest to smallest. The width of a row of components is capped at roughly half of the width of all drawn components' widths.

This PR also includes some internal changes to the scaling used for processing Graphviz layouts. Things are simpler now!

<img width="1922" height="1000" alt="flye_yeast" src="https://github.com/user-attachments/assets/155851eb-8de1-4d77-9db5-4c72393ae19e" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e996f2849a2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.