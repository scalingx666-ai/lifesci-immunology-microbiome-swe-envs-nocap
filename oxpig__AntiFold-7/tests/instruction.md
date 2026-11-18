# Issue

**Title:** Conda environment yml

## Description

I had quite a bit of difficulty installing dependancies. It seems there is a dependancy on pytorch-scatter that is missed. Also pytorch-scatter doesn't seem compatible with the version of pytorch you specify in your requirements. I created an environment.yml file that seems to fix these issues.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70df0df7128d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.