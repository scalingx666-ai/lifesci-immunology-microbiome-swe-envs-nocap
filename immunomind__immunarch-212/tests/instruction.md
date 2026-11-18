# Issue

**Title:** Germline algorithms update

## Description

1. Detect V.end and J.start automatically if missing;
2. Germline now contains reference sequences both for V and J chains;
3. Added warnings about too short V and/or J sequences;
4. Updated docs for repGermline.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6c41aff9720`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.