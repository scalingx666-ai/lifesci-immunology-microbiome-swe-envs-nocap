# Issue

**Title:** build: use packaged rocksdb instead of recompiling for dev

## Description

Use same solution from  to avoid re-building rocksdb, and instead linking to a pre-compiled system lib if available.

Update pixi and nix configs to provide it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `228aab7ee909`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.