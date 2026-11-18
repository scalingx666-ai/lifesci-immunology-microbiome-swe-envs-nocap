# Issue

**Title:** Release ARDA 2.37.1: batched correction searches

## Description

Prepare ARDA 2.37.1 with the merged correction batching fix: one native seqtree query batch per phase, allocation-aware correction CPU budgets, and pipeline forwarding. Parent assignments, error-rate formulas and reference/model parameters are unchanged.

Synchronize package versions, changelog and all four Nextflow/container pins. Focused release/correction checks: 29 passed; lint passed. The producing fix passed 1,405 local tests (nine optional OLGA skips), strict docs and full CI before merging as PR152. This release PR requires its own CI.

Publication follows seqtree 1.3.2, then vdjtools. No container image has been built or published by this PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6816b9206cee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.