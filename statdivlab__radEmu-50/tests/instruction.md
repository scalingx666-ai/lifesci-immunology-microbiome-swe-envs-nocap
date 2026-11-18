# Issue

**Title:** Address issue #48, intercept-only model

## Description

Make it possible to run intercept-only model with `emuFit`, while providing a message that the intercept will not be interpretable. Add a test in "test-emuFit.R" of intercept only model.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33008913ed3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.