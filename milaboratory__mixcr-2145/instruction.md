# Issue

**Title:** Raise per-mate V maxHits to 15 in amplicon align preset

## Description

## What

`align-amplicon` (`presets/blocks/01-align.yaml`): V aligner `maxHits` 2 → 15.

This is the per-mate candidate limit applied before R1 and R2 are combined. The combined limit
`align.parameters.maxHits: 5`, which also bounds the V hits stored in alignments and clones, is unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71e1fb33667e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.