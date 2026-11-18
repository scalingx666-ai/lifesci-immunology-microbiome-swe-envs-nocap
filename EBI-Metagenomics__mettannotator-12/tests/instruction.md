# Issue

**Title:** Fix ncrna

## Description

- Removed the duplication of rRNA detection (leaving only cmscan)
- Added tRNAscan-SE results to the final GFF
- Removed Infernal's tRNA calls from final GFF
- Added sorting of the final GFF

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `761e5a98ec8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.