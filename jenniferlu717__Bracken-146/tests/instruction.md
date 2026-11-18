# Issue

**Title:** Fix wrong include and refactor Makefile to build cleanly on macOS

## Description

@martin-steinegger asked me earlier to look over why his conda recipe was failing.
This resolves two of the problems that require conda patching ( you should be able to remove the osx.patch and ctime.patch in conda in the next release).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f11987228e4c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.