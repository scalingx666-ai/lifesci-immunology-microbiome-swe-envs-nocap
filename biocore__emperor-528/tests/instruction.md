# Issue

**Title:** Surgically add the EmperorViewController class

## Description

After starting the implementation of `AnimationsViewController`, I noticed that there would be a fair amount of repeated code between this new class, `AxesController` and `EmperorAttributeABC`, therefore I decided to move that redundant code to a new base class `EmperorViewController`.

This new class understands what a decomposition view dictionary is, but doesn't really alter the functionality that EmperorViewControllerABC provides. The tests and most of the code were extracted from `EmperorAttributeABC`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d1bb6068d57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.