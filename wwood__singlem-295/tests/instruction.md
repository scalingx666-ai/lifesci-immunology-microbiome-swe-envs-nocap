# Issue

**Title:** Multithreading + logging update

## Description

Refactored DIAMOND taxonomic assignment to spawn multiple diamond instances instead of using DIAMONDs internal parallel processing. This avoids non-deterministic memory allocation errors when thread count is high.

Also cleaned up the default logging by moving some more technical details to debug.

Added a spinning progress indicator to the prefilter step.
Added progress bars to sequence assignment and taxonomic assignment steps.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08f5a0672f9b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.