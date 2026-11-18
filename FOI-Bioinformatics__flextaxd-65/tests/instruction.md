# Issue

**Title:** Various fixes, primarliy related to downloading genomes

## Description

- Added display message to user about missing genomes when creating a kraken2 database.
- Added informative text to the display message that occurs when no genome is found by FTD (most often this should be due to faulty naming).
- FTD now prompts the user to download missing genomes during execution. I changed this since last pull request (self-closed) to now use the FTD-function to download genomes. 
- Fixed faulty function-referencing outside of object
- Added exception (skip/ignore) to nodes that do not have a name (e.g., it occurs when building a database from GTDB)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b40e8ad5705`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.