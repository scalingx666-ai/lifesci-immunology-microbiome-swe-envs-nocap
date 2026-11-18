# Issue

**Title:** Support Prediction from PyGAM LogisticGAM

## Description

PyGAM returns one set of probabilities unlike sklearn which returns 2. The automatic [:,1] in associated with the output of the exposure_machine_learner prevents using LogisticGAM. Other than that, they can integrate seamlessly since it largely follows the sklearn style. I added a simple check of the dimensions of the ndarray which either indexes into the array in the case of more than 1 dimension or directly returns the array when there is only one dimension. It's a pretty simple change but allows us to use a super powerful library.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b5b4ed81933`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.