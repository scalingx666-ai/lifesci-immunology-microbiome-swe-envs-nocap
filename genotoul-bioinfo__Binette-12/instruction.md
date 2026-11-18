# Issue

**Title:** Improve error management

## Description

This small PR improves error management by ensuring that all contigs from bins are found in the input contig file. Previously, missing contigs would cause Binette to fail with an obscure error message (see issue #11).

Additionally, this PR addresses the macOS GitHub runner crash in the GitHub Actions. The crash was due to "macos-latest" transitioning to macOS 14 with runners using the OSX-arm64 architecture, which is currently unsupported in Bioconda.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f7f213887e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.