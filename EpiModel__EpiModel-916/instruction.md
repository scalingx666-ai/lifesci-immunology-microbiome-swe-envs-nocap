# Issue

**Title:** make ergm.ego as a suggestion

## Description

ergm.ego as a suggest reduces the amount of dependency, especially `igraph` (through `tidygraph`) which is a pain to install on the HPC

- add a msg to the netest call when `ergm.ego` is not present
- fix the tests
- update the exports

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5f65a6058e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.