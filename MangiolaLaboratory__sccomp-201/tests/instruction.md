# Issue

**Title:** Add print method for sccomp objects and related functionality

## Description

- Implemented a new print method for sccomp objects to provide a summary of model specifications, data dimensions, and convergence diagnostics.
- Added helper functions for formatting output in the pillar package.
- Updated NAMESPACE to include the new print method.
- Created documentation for the print method in man/print.sccomp_tbl.Rd.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6f1aa11b665`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.