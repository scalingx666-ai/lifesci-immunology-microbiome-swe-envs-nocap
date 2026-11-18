# Issue

**Title:** Bug/pathofact2 200linescheck

## Description

This fix the issue #109 
I tested in a genome with >200 contigs and it worked.
Tests are passing without need to re-generate snapshots.
I have sneak in here a small change in the readme to explain the signalP license need.

Thanks for reviewing!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a0026589a0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.