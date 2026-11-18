# Issue

**Title:** Smooth arcs

## Description

This PR dynamically adjusts the number of line segments used to draw branch arcs. The number of line segments used to draw an arc is determined by the following formula: `min(60 * (total angle of the arc / pi), 2)` This formula seems to work fairly well on the trees I have tested and also greatly reduced the size of the buffer. On one of the larger trees I tested, the buffer used to draw the tree went from having 39208150 elements to 9230430 elements which is a ~4x smaller!

I also changed the default branch color to a darker grey color after our discussion on Tuesday.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d19f0dfd244`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.