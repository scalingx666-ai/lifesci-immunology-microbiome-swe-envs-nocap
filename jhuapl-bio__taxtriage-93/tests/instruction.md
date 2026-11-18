# Issue

**Title:** Compress names

## Description

- Updating multiqc to 40k rows
- Added fixed gap allowance for sourmash region merging
- Updated pathogen sheet annotations
- Re-added derived status for pathogen for a strain belonging to a known parent-level pathogen

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ebc38ac19e84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.