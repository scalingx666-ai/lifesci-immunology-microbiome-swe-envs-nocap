# Issue

**Title:** Improvements in the cell division demo

## Description

This PR concerns fixing and improving the demo that demonstrates the division of agents (representing biological cells in this example).
- highlighted the use of the pertinent model parameters for cell division, e.g., growth rate and maximum cell diameter to signal division;
- added the corresponding input parameter file that is usually represented by a "bdm.toml" file;
- provided a new demo, called as `cell_division_enhanced`, which builds on the existing `cell_division` one while it adds a bit more complexity to it by adding a user-defined "cell" type that has a dedicated way of multiplying (i.e., cell division).
- added ReadMe files that outline each demo - they provide important guidance how to run the demos and what to expect in the end.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2619fe542c5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.