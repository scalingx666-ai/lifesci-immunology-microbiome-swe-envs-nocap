# Issue

**Title:** Enable upload of data

## Description

Added a basic file upload field.
- The 'Clear' button removes the blob from the form, but does not delete the file on the server
- File is uploaded as a randomly named temp file
- Upload happens immediately after choosing the file to ensure that it exists at simulation execution time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb07a69acc81`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.