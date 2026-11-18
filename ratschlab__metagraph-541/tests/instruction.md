# Issue

**Title:** use 'top_labels' instead of 'num_labels' in metagraph-core api

## Description

Previously it was mixed: metagraph python api was using `top_labels`, and it was converting it internally before sending a request to the core metagraph http server, which was expecting that value by flag `num_labels`.
So, if one was sending requests to metagraph endpoints directly without using the python api, they would have to use `num_labels` instead of `top_labels`.

Now it consistently uses `top_labels` in both APIs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24859285ca3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.