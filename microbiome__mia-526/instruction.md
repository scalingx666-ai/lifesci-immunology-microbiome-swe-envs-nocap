# Issue

**Title:** Rename getTop*, getPrevalent*, getUnique* and get Rare* functions

## Description

This PR makes the following naming modifications :

- `getRareFeatures` --> `getRare`

- `getRareTaxa` --> `getRare`

- `getTopFeatures` --> `getTop`

- `getTopTaxa` --> `getTop`

- `getPrevalentFeatures` --> `getPrevalent`

- `getPrevalentTaxa` --> `getPrevalent`

- `getUniqueFeatures` --> `getUnique`

- `getUniqueTaxa` --> `getUnique`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1685435c1816`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.