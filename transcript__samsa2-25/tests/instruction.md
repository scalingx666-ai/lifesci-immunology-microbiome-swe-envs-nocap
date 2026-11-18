# Issue

**Title:** adding a checkpoint file

## Description

I propose adding a checkpoint file to the master_script.sh. This file will list each step as it is being processed. The point of the file is that if a particular step has already been run, when you re-run the main script, it will omit it from the pipeline, thus saving a lot of processing time rerunning the same analyses. Also, you can better troubleshoot when/if/where your analysis crashed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba23c12b96f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.