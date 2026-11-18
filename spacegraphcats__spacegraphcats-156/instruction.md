# Issue

**Title:** [MRG] Update to using latest khmer master.

## Description

khmer master has moved on, and some of the interfaces have changed; this PR updates to using the interfaces from the latest khmer master.

Note, requires  which is now in khmer/spacegraphcats branch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3069e46fb31d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.