# Issue

**Title:** macOS CI: unpin CMake on GHA runners to fix Homebrew conflict

## Description

Remove pinned CMake (local/pinned) on GitHub Actions macOS to avoid Homebrew conflicts. We uninstall CMake and untap local/pinned before running the installer.

Reference

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9d3c90e9716`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.