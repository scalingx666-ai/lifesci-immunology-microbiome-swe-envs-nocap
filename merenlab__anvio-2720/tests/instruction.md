# Issue

**Title:** Create test-base action

## Description

Coming from 

Resulting workflow seems to be working fine: https://github.com/merenlab/anvio/actions/runs/27152345582

I'm not sure about the zizmor ignore rule, but considering these changes doesn't introduce any new interface to execute code, I'm not sure if it's actually adding any risk.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06744c161081`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.