# Issue

**Title:** add translation qualifier to gff_to_gbk function

## Description

Hey @gbouras13 

I found that the`gbk` files generated did not have the `translation` qualifier which is useful in some downstream programs. I just added a couple of lines to the function.

Best.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92288cf2cc62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.