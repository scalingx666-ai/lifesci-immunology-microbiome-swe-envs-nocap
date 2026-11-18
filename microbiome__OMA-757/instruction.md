# Issue

**Title:** Update alpha diversity example

## Description

The example was modified to use the default indices returned by addAlpha():
dbp_dominance, faith_diversity, observed_richness, and shannon_diversity.  
All subsequent code chunks were updated so that the referenced index names match this output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a268c061d4a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.