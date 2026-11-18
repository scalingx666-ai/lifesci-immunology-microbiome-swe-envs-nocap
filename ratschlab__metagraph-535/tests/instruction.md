# Issue

**Title:** Updated Dockerfile

## Description

* ~~copy locally compiled htslib .so files to /usr/lib (since after  metagraph is linked against a locally compiled htslib)~~ not needed after . Now htslib is always linked statically.
* check if the binary runs fine
* removed unnecessary libs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24859b3d1e9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.