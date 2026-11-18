# Issue

**Title:** Fixes/cypress hardening

## Description

This fixes a few issues that lingered from the initial cypress setup:

- was pinned to a specific old release, install docs recommend broad pin to `v1`
- didn't include steps for uploading screenshots and videos for examining test results
- relied on a pretty arbitrary selector for the input elements that Streamlit seems to vary in random circumstances
- No fixed viewport size was configured for tests

Where nearly half my test runs were failing locally before, zero do now

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54c014f60c8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.