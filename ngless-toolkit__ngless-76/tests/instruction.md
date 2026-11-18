# Issue

**Title:** Catalogs and Pig reference genome

## Description

Catalogs for mouse, dog and pig.
Pig was not yet in the list of reference genomes.
It's added here under the identifier `susScr11`.

Dog and Mouse catalogs were tested.
Pig was not as ngless didn't yet recognize the `susScr11` identifier and I couldn't compile the changes to a binary compatible with our servers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `906c275bc888`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.