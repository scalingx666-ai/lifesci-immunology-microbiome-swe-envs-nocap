# Issue

**Title:** 1.0 Release

## Description

This is the beginning of the Dashing 1.0 release series. Future development will primarily be support rather than new features. For the latter, see [Dashing2](https://github.com/dnbaker/dashing2).

This adds support for xz- and bzip2- compressed files, and a switch to C++-17 requirements.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47f5c141ce31`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.