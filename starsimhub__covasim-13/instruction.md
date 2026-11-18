# Issue

**Title:** Fix webapp in docker, rename cova_webapp -> webapp

## Description

When the webapp was changed to run from `cova_webapp` to `webapp`, Docker was not updated.

This meant that docker failed to run the webapp appropriately.

These updates fixed the problems locally for me.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `742b1dea0d71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.