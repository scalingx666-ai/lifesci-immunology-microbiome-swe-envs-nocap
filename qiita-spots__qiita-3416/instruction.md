# Issue

**Title:** log user creation timestamp

## Description

Addressing #3378 this PR will use SQL's `NOW()` function to log creation of a new user account (validated or not). This is handy for:
a) reconstructing user growth
b) pruning accounts that have been created but not validated for X days

I've also added this information to the user's profile page, if the value is not None:
![image](https://github.com/qiita-spots/qiita/assets/11960616/3725d290-a143-416b-a044-0fd9bf3060ac)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cca6de70322f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.