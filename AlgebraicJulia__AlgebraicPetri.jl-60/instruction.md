# Issue

**Title:** Fix hardcoded parameter symbol in bilayer net compilation

## Description

You can see the bug even in the docs (picture below). The unit tests were passing due to an unfortunate coincidence in the local namespace.

<img width="710" alt="image" src="https://user-images.githubusercontent.com/316610/125147658-9232d380-e0e1-11eb-825b-05d5b1b733d5.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b8e7fb29b55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.