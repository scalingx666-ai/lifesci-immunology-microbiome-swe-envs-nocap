# Issue

**Title:** ENH: Minor improvements to biplots UI

## Description

- Improve raycasting for arrows. Previously it would also check for
intersects with lines, which would lead to incorrect matches.

- Fix biplot coordinates computation so that it doesn't modify the
original array, instead it creates a copy. Prevents us from modifying
the inputed OrdinationResults object.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9d787ff24c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.