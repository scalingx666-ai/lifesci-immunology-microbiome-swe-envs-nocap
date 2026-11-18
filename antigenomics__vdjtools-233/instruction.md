# Issue

**Title:** Release vdjtools 5.9.0

## Description

Release vdjtools 5.9.0 with exact mixed G/P/N codon-origin posteriors and matching local immutable-template constraints on the existing masked Pgen API.

The release tree is identical to feature 9e1ddfa3 (tree 82742411127f1ebb4cca8cc4e899dd3ede410502), which passed all six CI jobs in run 41385824620. Local verification includes 1,887 release-tier tests, both C++ tests, zero-warning docs, 42 clean-wheel checks and 268 byte-identical bundled model assets. Final serial/16-thread fixture results are bitwise equal with 10.65–10.85x speedups.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aaa27fa5f0fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.