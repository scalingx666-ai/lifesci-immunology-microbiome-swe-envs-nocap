# Issue

**Title:** 200 minhash limits high count in dilution series for similar strains in a species

## Description

Merging fix for the strain to species/genus tass scores where higher ranks would have the reads removed and negatively impact the overall tass at that level. 

Added some html features in the report including:

- Tooltips for various features
- An update to the summary tab to annotate classification level
- Export to pdf is updated as a small button at the topright of the panel
- Fix some custom data loading issues with the summary tab

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3af9f4523f1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.