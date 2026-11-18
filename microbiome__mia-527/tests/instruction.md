# Issue

**Title:** Rename perSampleDominant* to getDominant and addPerSampleDominant* to addDominant

## Description

This PR makes the following naming modifications : 

- `perSampleDominantFeatures` --> `getDominant`

- `perSampleDominantTaxa` --> `getDominant`

- `addPerSampleDominantFeatures` --> `addDominant`

- `addPerSampleDominantTaxa` --> `addDominant`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc5c228f8c5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.