# Issue

**Title:** Enumerate BOSS sink dummy edges with rank/select

## Description

Enumerate BOSS sink dummy edges with rank/select instead of scanning every edge, preserving the count-only path and existing mask bits. Assert the two leading sentinels and start one-based select at occurrence 3.

Include regression coverage for all four BOSS states, empty graphs, small paths and pre-populated masks, plus a benchmark of the production method including mask allocation. This is an AI-assisted extraction of Gunnar's .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ee1a3a2c997`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.