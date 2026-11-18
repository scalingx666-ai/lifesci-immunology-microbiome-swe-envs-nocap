# Issue

**Title:** Fix bad assumption in `oapply_typed`

## Description

. Note that the fix requires exposing the junctions in the UWD through outer ports, hence is also a breaking change. See the changes to the unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0afbc1a8adad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.