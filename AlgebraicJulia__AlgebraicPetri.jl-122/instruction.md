# Issue

**Title:** Flatten ACSetTransformations

## Description

This adds:

- some customization ability to the `flatten_labels` function
- the ability to flatten the labels of ACSetTransformations
- Generalized `typed_product` to work for more than two petri nets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `63e5d066f311`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.