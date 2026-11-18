# Issue

**Title:** Fix issue #32

## Description

Instead of using the `mvdb` module, just unzip DB.tar.gz in the destination directory.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea7f5c0240d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.