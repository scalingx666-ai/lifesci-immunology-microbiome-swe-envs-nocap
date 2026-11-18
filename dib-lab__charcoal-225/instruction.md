# Issue

**Title:** [MRG] fix `LCA_Database.gather(...)` call to use `LCA_Database.best_containment(...)`

## Description

In  I renamed `Index.gather` to `Index.best_containment`, and that broke charcoal.

This PR fixes that, adds a test, and also:
* updates sourmash to v4.4.3.
* updates python to >= 3.8

Fixes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc97e9839816`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.