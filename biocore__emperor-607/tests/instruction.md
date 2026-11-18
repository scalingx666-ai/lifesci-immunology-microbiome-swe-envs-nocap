# Issue

**Title:** BUG: Avoid double/triple/quadruple clicks

## Description

~~**This PR depends on #606, so merge that one first.**~~


Fixes a problem with attribute editors requiring more than a click to
reactivate after changing value. For example users could change the
color of "Category A", after changing the color and then clicking on the
same "Category A" to change the color again, users would sometimes need
to click awkwardly until the editor reappeared on screen.

This bug affected all editors (color, visibility, scale and shape).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1eac483e2ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.