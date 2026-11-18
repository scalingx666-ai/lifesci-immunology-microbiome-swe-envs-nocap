# Issue

**Title:** Refactor graphics framework for easier extension

## Description

This PR adds the ability to define state/transition node generator functions. This prevents a lot of repeated code that handles the wiring between nodes and will hopefully increase consistency between the multiple things we can visualize on a graph (heatmap over transitions/states, restricting positions of certain nodes, subobject highlighting, etc)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d20e2889d566`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.