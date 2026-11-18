# Issue

**Title:** BUG: Fix problem with custom axes

## Description

Both for procrustes and for jackknifed plots setting a custom axis would
lead to a failure, specifically:

- Procrustes plots would error since the sample identifiers would be
relabeled twice.

- Jackknifed plots would fail (on JavaScript) because the confidence
intervals didn't have the same dimensions as the coordinates themselves.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9978ccee6449`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.