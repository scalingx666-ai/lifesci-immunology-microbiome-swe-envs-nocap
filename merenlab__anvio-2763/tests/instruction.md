# Issue

**Title:** Update structure db colabfold

## Description

Now the 4th PR after #2755 (colabfold driver + minimum integration), #2759 (update display), #2760 (add --only-msa/--only-predict checkpoints) regarding the integration of colabfold in anvi'o.
This time, it is about adding colabfold into the program `anvi-update-structure-database`.

What it does: mirror the way MODELLER update already work. The parameters (num models, num recycle, ambler, colabfold msa source, colabfold additional parameters) are read from the structure database itself and reused, so an update stays consistent with the original run. Only the 'machine' specific parameters needs to be resupply like colabfold conda env, colabfold database and the optional checkpoints.

Right now it refuses to change the MSA source. If the user used a local colabfold database, they cannot update the structure db by asking to use the public MSA server. I understand that this could be a debatable choice. I went conservative here, although i cannot check if a local colabfold database it the same as in the original run.

Updated the test as well, which now takes a really long time to run (>30 min on the HPC, with 100 CPU to test the checkpoints, and with GPU).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3f8bc3f334e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.