# Issue

**Title:** ENH: Add synchronized animations

## Description

In an Empire plot, users can start an animation in Emperor, and the tree will
update synchronously with the trajectories. Only points in the gradient are
visualized in the tree.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5076faee387`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.