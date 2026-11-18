# Issue

**Title:** Enable GEE with working independence

## Description

Allow cluster dependence / GEE using the newly added 'cluster' argument for emuFit. Only working independence between rows of Y is supported.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13dd0b1aec76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.