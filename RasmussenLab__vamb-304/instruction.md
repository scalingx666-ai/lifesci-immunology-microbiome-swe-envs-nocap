# Issue

**Title:** Add stderr logger early in main

## Description

Because we remove the default logger on init, but only add the new logger when run() is called, there is no logger available during the preprocessing steps, e.g. argparsing.
This leads to warnings not being shown to the user, which is very bad from a usability point of view.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a9d06162be7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.