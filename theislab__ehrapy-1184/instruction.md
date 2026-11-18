# Issue

**Title:** Seed the models of the causal meta-learners with random_state

## Description

The S-, T- and X-learners take `random_state=0`, which together with the existing `random_state` of the effect estimators seeds the built-in gradient boosting and random forest models, so CATEs and effects from these models are reproducible.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca5411ea91e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.