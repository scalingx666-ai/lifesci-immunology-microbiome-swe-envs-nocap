# Issue

**Title:** fix 3222 via fp_type

## Description

The  relied on filenames, which meant that every new file (which depends on the plugins) needed to be added. This PR does the same but via the `fp_type`, which should substantially should reduce the need of adding new names.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4b6fcb0248b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.