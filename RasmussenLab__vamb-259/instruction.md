# Issue

**Title:** Output cluster metadata in separate file

## Description

The overall idea here is that we output more metadata about generated clusters, allowing our users to more easily get an idea of the cluster quality.

I would like to ping off ideas around this with you guys.



Based on #251, though the changes are small enough that they can be cherry-picked to existing master if necessary

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62baa3582dc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.