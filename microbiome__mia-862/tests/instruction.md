# Issue

**Title:** Add getDysbiosis and addDysbiosis

## Description

Adds getDysbiosis and addDysbiosis: median dissimilarity of each sample to the controls (Lloyd-Price et al. 2019), excluding the sample itself and optionally samples of the same subject. .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77707c0d2e81`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.