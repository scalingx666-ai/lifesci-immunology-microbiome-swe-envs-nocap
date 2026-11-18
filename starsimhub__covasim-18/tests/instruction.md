# Issue

**Title:** Respect autoreload argument in cova_app.py

## Description

Probably not THAT important since it only has an effect when using `launch_flask` in background mode (or invoking manually with `python3 ./cova_app.py <port> <autoreload>`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cfc73005f97a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.