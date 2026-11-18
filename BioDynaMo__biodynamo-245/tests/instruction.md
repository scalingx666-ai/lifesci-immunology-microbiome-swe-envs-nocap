# Issue

**Title:** Add quality checks with `Sonar Cloud`

## Description

This PR (+some invisible work behind the scenes) brings `Sonar Cloud` source code checks to the BioDynaMo repository. The results of the analysis are available via a [dashboard](https://sonarcloud.io/project/configuration?id=BioDynaMo_biodynamo) accessible for all to see and for all developers to take action.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9496b66bc471`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.