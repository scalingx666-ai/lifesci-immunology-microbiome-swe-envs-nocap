# Issue

**Title:** Remove TreeNode from the main workflow

## Description

Use BPTree for all operations. In addition, I also removed the usage of
"EmpressNodeXXX" to refer to unnamed nodes.

This resulted in a lot of code being deleted, and a few tests being removed
since bp.parse_newick differs from TreeNode.read. The biggest thing being that
missing length values are by default assigned to 0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `054987494548`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.