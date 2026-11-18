# Issue

**Title:** Fixing taxonomic profile generation

## Description

a) If a rank is missing in the taxonomy, add an empty "slot" in the taxpath: ||
b) If a genome has 0-abundance, it does not appear in the profile anymore
c) dry-run option

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `944a232089fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.