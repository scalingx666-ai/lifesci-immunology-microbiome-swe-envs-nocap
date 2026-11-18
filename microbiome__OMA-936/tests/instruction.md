# Issue

**Title:** Bump version to 1.1.12 so CI installs the new dependency

## Description

Fixes the failing `ubuntu-latest (auto)` check on #882.

**Cause:** the CI restores a cached R library and then skips reinstalling OMA and its dependencies, because the package version has not changed:

> Skipping install of 'OMA' from a local remote, the SHA1 (1.1.11) has not changed since last install.

The new `tidySummarizedExperiment` dependency (added in #935) was therefore never installed, and R CMD check failed with:

> Package suggested but not available: 'tidySummarizedExperiment'

**Fix:** bump the version in `DESCRIPTION` from 1.1.11 to 1.1.12, so that the CI installs the dependencies again.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3f12f4c691f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.