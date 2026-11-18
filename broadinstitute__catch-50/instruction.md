# Issue

**Title:** Fix crash on macOS with Python 3.8+

## Description

This . See 2a548e8.

This PR also makes some changes to Travis CI's configuration file in an attempt to add testing on macOS, but reverts those changes. Getting macOS testing to work, especially with recent version of Python (3.8+), seems like it will be a more complicated undertaking than it might be worth.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e40890b2b02a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.