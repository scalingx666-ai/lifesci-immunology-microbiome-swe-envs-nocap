# Issue

**Title:** Remove prime fix

## Description

This fix will allow for any arbitrary number of sample categories to be colored. I also changed the way names are handled. Before, I assumed all branch names would be unique however, I noticed that some tree do not have unique branch names. So, I created an additional structure that takes in a name and returns a list of all branches associated with it. Also, I now use post-order positions as an index into treeData because names are no longer assumed to be unique.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e29e4c48994`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.