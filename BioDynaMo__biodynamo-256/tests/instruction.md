# Issue

**Title:** Update flocking demo with local fluctuations

## Description

Introduced local fluctuations to the flocking parameters depending on space and time. Added behavior for white noise disturbances as well. 

**Goal:** Flocking demo should look more dynamic and not completely stable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe34ced0f537`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.