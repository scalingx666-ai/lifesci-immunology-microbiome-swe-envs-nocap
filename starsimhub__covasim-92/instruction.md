# Issue

**Title:** add hyper parameter sweeps with Weights & Biases

## Description

Please review @cliffckerr @inc0 

related to:  

## Summary of changes

- Updated the README with Instructions
- Added Table of Contents to the README
- Added a directory `/sweep` which adds the code and configuration files for the example sweep.
- You can see example sweeps for this project at https://app.wandb.ai/github/covasim/sweeps

![image](https://user-images.githubusercontent.com/1483922/78935156-0acf5e00-7a61-11ea-84d6-84a5621362e8.png)

### Aside - Weights & Biases

- It is free for open source projects, so should be perfectly fine for other people who want to set this up. 
- These are the docs for sweeps: https://docs.wandb.com/sweeps
- This is pricing:  https://www.wandb.com/pricing

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b55f28cdaba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.