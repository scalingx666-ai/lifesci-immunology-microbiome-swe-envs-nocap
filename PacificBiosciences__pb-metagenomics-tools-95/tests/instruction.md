# Issue

**Title:** Add all bin summary

## Description

**HiFi-MAG-Pipeline**
Created new summary file that includes all bins (including those that fail):
- Reports CheckM2 information for all bins created by DAS_Tool 
- These bins are a combination from SemiBin2 and MetaBat2 
- Labeled as `Pass` or `Fail` based on QC thresholds 
- Useful for inspecting characteristics of bins that failed QC

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af66f9511320`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.