# Issue

**Title:** The updated code according to the developer's advice, to fit eukaryotic plastid screening

## Description

Hi Ben and singleM team,

After talking with Ben several times I reformed the code of my branch, to change the code mainly in condense.py to solve the issue with:
1. error in writing information to otu when prokaryotic taxa are considered as off-targets (in my context, which deals with plastid/eukaryotic sequences);
2. target_domain detection in genus-wise EM that causes zero-division errors.

Now, feel free to review it, and feel free to notify me/deny my pull request. 

Cheers
Andy

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a5f867391ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.