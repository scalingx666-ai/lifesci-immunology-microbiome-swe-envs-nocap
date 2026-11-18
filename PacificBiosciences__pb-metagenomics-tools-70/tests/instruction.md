# Issue

**Title:** HiFi-MAG-Pipeline: Upgrade minimap2 to 2.26

## Description

I also ran into #67. Upgrading to 2.26 resolved the issue for me.

- Upgrade minimap2 to `2.26` for `map-hifi` support.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d250602e5c19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.