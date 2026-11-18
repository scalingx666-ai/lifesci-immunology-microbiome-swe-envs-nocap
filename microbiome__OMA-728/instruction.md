# Issue

**Title:** Move tutorials to miaDemo repo

## Description

Related to this issue  and this PR 

Maintaining these tutorial workflows with multiple languages is hard in OMA as there are higher quality standards and everything should be up-to-date. miaDemo repository is natural place for these as it contains tutorials and demonstrations that we have run in several occasions.

This PR removes tutorial workflows from OMA.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73975f56c67b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.