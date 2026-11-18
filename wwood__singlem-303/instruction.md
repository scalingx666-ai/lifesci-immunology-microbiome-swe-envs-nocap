# Issue

**Title:** feat(pipe): deduplicate read windows before DIAMOND blastx fallback

## Description

Identical 60bp windows from abundant organisms were sent to DIAMOND individually. Now one representative per unique window is BLASTed and the result propagated to all originals, cutting DIAMOND calls in proportion to sample novelty / smafa failure rate.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52e3e36d90fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.