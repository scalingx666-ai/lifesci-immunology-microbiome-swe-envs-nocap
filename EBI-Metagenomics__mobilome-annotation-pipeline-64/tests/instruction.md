# Issue

**Title:** Setting the amrfinder_plus databases as a path

## Description

This change is necessary to fix the issue #58. The amrfinder process is not handling the database as a path so it's not mounting the directory properly in your system (or any system using docker/singularity).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `664199068edf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.