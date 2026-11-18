# Issue

**Title:** CI: fix dependabot config syntax, and clippy beta lints

## Description

Fix a config syntax mistake from #3749, and address new clippy beta lints

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed3a254640c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.