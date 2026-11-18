# Issue

**Title:** Update macOS support 10.15, 11.6, 12.latest

## Description

Agreed to support 10.15, 11.6 with latest Xcode (arm64 & i386), and 12.latest. This PR fixes the SHA256sums and informs the users that 11.x (x<6) is not officially supported. Further, we commented out the caching of third parties in GHA because it sometimes takes 4-5 minutes which is slower than downloading.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8906a955bde`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.