# Issue

**Title:** Display structure colabfold

## Description

Second PR regarding the integration of ColabFold in anvi'o (follows #2755).
This time it is about making anvi-display-structure compatible with colabfold-made structure database.

The display is now engine aware (MODELLER or ColabFold) and shows values related to one or the other engine, like mean pLDDT for ColabFold (does not exist for MODELLER) and also color residues by their pLDDT score.

Include a couple of fixes in the test, as well as an update of the test down to the visualization.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98eeb32be237`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.