# Issue

**Title:** Updates for issue 18,19,20.

## Description

Added functionalities
- ```database-report```: It takes ```acc2taxid.map``` (A result file of ```build``` and provided in pre-built DBs) to generate taxonomy report of a database.
- ```--mask``` and ```--mask-prob``` options of ```classify```: You can mask low-complexity regions with ```--mask 1``` and set the minimum low-complexity probability with ```--mask-prob 0.X```. We are using ```tantan``` for the masking.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49f80207318c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.