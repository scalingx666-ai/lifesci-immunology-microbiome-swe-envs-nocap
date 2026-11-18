# Issue

**Title:** BUG: Fixes color distortion for flat-facing geometries

## Description

Geometries that are flat-facing would suffer from color distortion. To
fix this, I've added a small amount of rotation to those geometries. And
included a few new geometries.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f002f2e4ec84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.