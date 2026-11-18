# Issue

**Title:** Cite ReducedExperiment in data containers chapter, refs #748

## Description

Adds a short note in the Data containers chapter, next to the `reducedDim`
description, explaining that ReducedExperiment stores reduced data together
with feature loadings, with the citation.

Scope follows @0xMuluh's guidance in #748: citation-only first; no new code
chunks or dependencies.

@0xMuluh @TuomasBorman

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a33442b2c643`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.