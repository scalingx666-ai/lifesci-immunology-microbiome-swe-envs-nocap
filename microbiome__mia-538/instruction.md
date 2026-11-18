# Issue

**Title:** Move functions replaced by transformAssay to deprecate file

## Description

This PR moves all the deprecated functions replaced by `transformAssay` to the deprecate file.

Here are the functions targeted : 

- `transformFeatures`
- `transformSamples`
- `transformCounts`
- `relAbundanceCounts`
- `Ztransform`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e53f76986b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.