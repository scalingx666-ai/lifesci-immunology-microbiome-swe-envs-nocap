# Issue

**Title:** bug fix for large refs

## Description

Given a reference longer than 4Gb, minimap2 is unable to see all the sequences and thus can't produce a correct SAM header. This throws an error in the `MinimapToBam` rule with the sorting step. This fix avoids the issue by splitting this rule into two new rules: `MinimapIndex` and `MinimapToBam`. These rules index the reference prior to alignment and run minimap2 with the `--split-prefix` option, respectively.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e8307ccaf9b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.