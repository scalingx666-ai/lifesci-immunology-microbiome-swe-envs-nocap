# Issue

**Title:** Take a trainer in ep.ml.fit

## Description

ep.ml.fit takes a trainer that sets how deep learning models are trained, including torch modules passed as model. Custom torch modules such as a SAITS backbone can now be trained with other epochs, batch sizes, class weights or devices than the defaults.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bac1cc3a163f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.