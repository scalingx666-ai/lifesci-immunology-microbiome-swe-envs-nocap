# Issue

**Title:** removed requirements.txt from the readthedocs.yml file

## Description

Tested the build on Read the Docs and this fixes the dependency error seen yesterday. 
<img width="616" alt="covasim-fix" src="https://user-images.githubusercontent.com/20909236/92943799-73f03e80-f410-11ea-84f5-61db96207387.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15862eebc251`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.