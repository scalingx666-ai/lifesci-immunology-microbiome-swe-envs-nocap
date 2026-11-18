# Issue

**Title:** Remove `benchmark` from default build target

## Description

We deactivate the `benchmark` build target by default to save time in the build time for developers and users. The option is explicitly activated in GHA to make sure that they keep compiling and do not get out of synchronization with the core of the repository.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b86794ed8ff0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.