# Issue

**Title:** Release 5.3.2: verified corpus bootstrap and bounded sample PCA

## Description

Release 5.3.2 fixes corpus bootstrap integrity and bounds sample-PCA application memory.

Validate immutable paired corpus payloads on every indexed lookup, coordinate downloads with a crash-releasing process lock, and preserve verified legacy/offline caches. Apply sample rotations in bounded row blocks and expose the existing numerical CPU budget during CLI fit/application.

Validation: PR219 and PR220 each passed all six CI jobs, including full Linux Python 3.12 coverage. Focused bootstrap/projection checks and strict Sphinx builds passed. Published seqtree1.3.2 and arda-mapper2.37.1 remain the verified upstream dependencies. This promotion contains no fitted-model changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60949492524d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.