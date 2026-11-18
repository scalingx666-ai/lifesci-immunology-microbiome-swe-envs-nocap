# Issue

**Title:** doc/ permissions; rsync support for improved download times

## Description

The install target currently creates an empty doc/ dir in $(prefix)/share/centrifuge/doc
with permissions 644 and also changes the source tree's doc dir to this permissions; the
actual documentation is never installed.

In addition, this is done several times..fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3d2e84c168f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.