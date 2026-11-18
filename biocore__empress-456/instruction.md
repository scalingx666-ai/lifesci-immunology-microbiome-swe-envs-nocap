# Issue

**Title:** NEW warn when layout options (approximately) do not change branch lengths

## Description

.

This PR follows up on #444 to raise a toast message if the tree is not changed by options like "make ultrametric" and "ignore branch lengths".

When working on a tree from qemistree (thanks @gibsramen ), I found that the branch lengths could be modified by small amounts by the make ultrametric code, but this resulted in no visible difference between the two trees. As a result, I introduced a tolerance for how similar branch lengths should be in order to make this warning. Though this could result in a warning being falsely raised in the case where the branch lengths in the tree are all very small.

![Screen Shot 2020-11-25 at 11 05 42 AM](https://user-images.githubusercontent.com/19470970/100271354-3890e680-2f0e-11eb-8145-abe1891cae6d.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ba5b7d46ef5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.