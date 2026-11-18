# Issue

**Title:** Add `bdm view` to CLI

## Description

Add a wrapper for opening the latest ParaView state for a smoother development workflow.

Workflow including visualizing:
```
# Branch specific setup
cd <path-to-my-bdm>
git pull
git checkout bdm-view
cd build
cmake .. & make -j <num-cores>
. bin/thisbdm.sh
cd <some-directory-you-like>
# Workflow
bdm demo soma_clustering
cd soma_clustering
bdm run
bdm view
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1dc64eed183`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.