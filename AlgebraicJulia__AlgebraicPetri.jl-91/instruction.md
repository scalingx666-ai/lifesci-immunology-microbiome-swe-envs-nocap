# Issue

**Title:** Add SubACSets.jl for mca

## Description

This fixes  and would remove the necessity of  by fixing the dependency setup. Note that the known issue of  is not fixed, though it's unclear if this is a major issue.

Note I didn't know what tests to add. @p-stokes can you add an appropriate test here, or point me to a code to create a test from?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e55c792de50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.