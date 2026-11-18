# Issue

**Title:** Minor improvements to DAA and mediation sections

## Description

In this PR:
- replaced ggplot with plotForest in DAA chap
- corrected description of Tengeler2020 (mice, not human samples)
- added minimal theme to mediation plots

Remarks:
- ideally theme_minimal would be added to plotLoadings and plotMediation functions
- broken ref to ?sec-daa_extra in DAA chap, which is not rendered

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ef42ffcec8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.