# Issue

**Title:** Bugfix: Correct number of elements in AAMB dataloader

## Description

Commit 5c1dc3e added another feature to Vamb, namely absolute abundances. AAMB, however, does not (yet) use this feature. However, it still uses the same data- loader Vamb does. Hence, it failed when it tried to iterate the dataloader with the wrong number of elements.
The bug is fixed in this PR, but there are several underlying issues here that need to be fixed:
* The AVAMB installation instructions recommended installing Vamb from the master branch. This has also been changed in this PR to install the latest version.
* There are no tests for AVAMB, meaning regressions like these go unnoticed.

 

CC @Paupiera - can you run a simple AVAMB workflow and verify that it still works? Maybe just a few epochs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `213973cfb857`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.