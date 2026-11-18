# Issue

**Title:** Improve mechanism to reuse the index part of AgentUids

## Description

The new mechanism uses thread-local vectors of AgentUids whose index can be reused.
This mechanism requires less thread synchronization than the previous solution and improves performance.

Add IO capabability for bdm::SharedData.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72ea93433f71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.