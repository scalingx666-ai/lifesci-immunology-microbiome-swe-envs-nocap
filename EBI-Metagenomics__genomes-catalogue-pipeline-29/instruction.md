# Issue

**Title:** Kraken step

## Description

* Added step 9 that generates new databases and resources (kraken2 + bracken, phylogenetic tree, mash sketch, gene database, virify annotations)
* Moved original step 9 (restructuring) to step 10 and made modifications to accommodate tool version changes and files generated in step 9

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8b182f04b0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.