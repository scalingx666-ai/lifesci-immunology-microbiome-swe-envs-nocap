# Issue

**Title:** Another large refactoring, this time with direction and purpose.

## Description

* switch `compare_taxonomy` over to doing single genomes
* implement CSV combining via a fairly simple script that does nice error reporting

TODO:
- XX add github actions to run tests - punted to #159

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71265a92a2c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.