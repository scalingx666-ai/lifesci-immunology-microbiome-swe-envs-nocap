# Issue

**Title:** [WIP] Add back AGP (scaffold) file visualization; other improvements

## Description

AGP visualization needs to be fixed to handle searching for nodes within collapsed patterns (currently it gives up when trying to highlight a scaffold where all nodes are not immediately visible). And, like searching, it should also be made to handle duplicate nodes properly. I think at least the first of these should be addressed before adding this in.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3690bccd38b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.