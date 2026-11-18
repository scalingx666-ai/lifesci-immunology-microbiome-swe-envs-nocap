# Issue

**Title:** Fix 364

## Description

. This implements a binary search and also limits the number of suggestions to 10 ids

Here is a link to the improved [version](https://view.qiime2.org/visualization/?type=html&src=https%3A%2F%2Fdl.dropbox.com%2Fs%2F7xrpr6z8vzoot24%2Ffast_autofill.qzv%3Fdl%3D1) and here is a link to the original [version](https://view.qiime2.org/visualization/?type=html&src=https%3A%2F%2Fdl.dropbox.com%2Fs%2F9ybj0aqtj0nhajz%2Fslow_autofill.qzv%3Fdl%3D1).

You can test them by searching for 'taag' in the node search box.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc146db32fe0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.