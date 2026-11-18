# Issue

**Title:** Read multiple datasets from one file

## Description

This will add a utility function to read all frames contained in a single `.fcs` or `.lmd ` file, see .
If such a file is opened with `FlowData()` a `MultipleFramesDetectedError` exception is thrown, so any tools can indicate that they should use `flowio.utility.read_multiple_flowframes()` in order to get all contained frames in a list.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec5bd99495cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.