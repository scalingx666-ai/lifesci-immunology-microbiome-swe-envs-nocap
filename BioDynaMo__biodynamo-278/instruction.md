# Issue

**Title:** Demo monolayer growth

## Description

Added monolayer growth demo that simulates the growth of a 2D monolayer as the cells proliferate. Cells go through a whole cycle (G0/G1 -> S -> G2 -> M) and duplicate when their volume has doubled. The growth of the monolayer replicates the experimental data shown in Figure 1 from Drasdo and Hoehme (2005).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8afcefdf382`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.