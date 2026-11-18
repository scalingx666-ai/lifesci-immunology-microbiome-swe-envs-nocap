# Issue

**Title:** Update the syntax for qwraps2::summary_table for qwraps2 version >= 0.5.0

## Description

Prior to qwraps2_0.5.0 the use of the .data pronoun was encouraged.
With the release of version 0.5.0 of qwraps2 the use of the data pronoun
is no longer needed or encouraged.

This change updates the syntax in the vignette and version in the
DESCRIPTION file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08334b8beb25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.