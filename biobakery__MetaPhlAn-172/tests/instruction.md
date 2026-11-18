# Issue

**Title:** Use tempfile for marker file for extract_markers.py

## Description

Hello Aitor and Francesco,

The bioBakery workflows can run multiple extract_markers.py tasks at once, one for each species selected for the StrainPhlAn runs. I noticed there existed a race condition where these tasks will all try to write and then read from the same temp markers file since the workflow places all of the markers in the same folder. It does this in part because it does not know the name of the species until each task is run so part of the command has to be dynamic. 

I made a really small change to the extract_markers.py function "generate_markers_fasta" to write to a tempfile. This will resolve the race condition as all of the temp files should have unique names. 

Please check it out and let me know what you think. 

Thank you!
Lauren

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ab8f35d3701`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.