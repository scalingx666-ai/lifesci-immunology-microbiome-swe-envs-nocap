# Issue

**Title:** Add general API section intros and redirect removed tutorials

## Description

Adds short general introductions to API reference sections and redirects the pages of deleted tutorials to the tutorial gallery with sphinx-reredirects. Links to the removed notebooks keep working once the tutorials submodule drops them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `269c6bb07f8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.