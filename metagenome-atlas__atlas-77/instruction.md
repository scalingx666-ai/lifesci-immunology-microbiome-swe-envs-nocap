# Issue

**Title:** Cluster submission

## Description

@brwnj  Could you check this. 
I started changing for the cluster submission. the BBtools need always 15% of overhead therefore I added the java_mem ressource keyword. 

I added also the atlas QC workflow, which produces a bug, but I have a hard time to debug the click scripts.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c9fa0bb77ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.