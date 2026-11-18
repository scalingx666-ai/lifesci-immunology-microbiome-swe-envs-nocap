# Issue

**Title:** Release vdjtools 5.8.0: joint N-region masked Pgen

## Description

Adds optional exact joint N-region constraints to the existing scalar and batched degenerate amino-acid Pgen APIs. Unconstrained calls and bundled model parameters remain unchanged.

The merged source tree matches PR #230, where all six CI jobs passed. Local checks: 1,876 Python tests passed; both C++ tests and strict documentation passed. A clean wheel installation passed 31 origin/degenerate/golden tests. Joint-interval tests distinguish a joint origin probability from a product of marginal site probabilities.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2bfbc5df677`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.