# Issue

**Title:** Webapp interventions

## Description

Implements functional interventions for the webapp. Not extensively tested, but seem to work. This PR builds off of (and includes) PR 

This version is currently live at https://covid.idmod.org/sim

Closes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53f288d75616`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.