# Issue

**Title:** Improve Error Handling for Version Hash Conversion in MMseqs2

## Description

MMseqs2 uses a versioning scheme that combines a major version number with a shortened commit hash. Attempting to cast this commit hash to an integer frequently triggers errors that provide less clarity than the subsequent logging error messages (see issues #356, #363).

Keeping the `mmseqs_minor_version` as a string prevents this error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb9f1f4d9b8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.