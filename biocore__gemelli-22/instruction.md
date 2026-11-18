# Issue

**Title:** fix broken pypi dist build

## Description

This fixes issue #21 -- the MANIFEST.in was missing which caused the distribution build to miss the citations.bib file. This, in turn, caused the upload to pypi to break the QIIME plugin.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82822166df3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.