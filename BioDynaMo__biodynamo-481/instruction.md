# Issue

**Title:** Preserve ParaView state files across headless rendering failures

## Description

Save a preliminary state before updating animation timesteps and save again after a successful update to retain the complete time range. Request offscreen rendering and keep pvbatch failures fatal when no state file was produced.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `553f69cb6ddf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.