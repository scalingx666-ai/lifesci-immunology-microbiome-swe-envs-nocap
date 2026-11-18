# Issue

**Title:** Update run_RF and a gpu-related option in the configuration

## Description

1. Revise run_RF.py into run_RF.py.py; 
2. Add "--gpu" for run_metapi.py init 
- choices: ["true", "false"]
- default: "true"
- required: false
If specified as "false", set "cuda: false" in config.yaml

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc1425e15599`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.