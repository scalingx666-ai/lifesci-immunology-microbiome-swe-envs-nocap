# Issue

**Title:** Add option to shear tree-plot to feature metadata

## Description

Relevant to #419. Currently implemented only in `tree-plot` not `community-plot`.

Adds the `--p-shear-to-feature-metadata` parameter to `tree-plot`. This parameter, if set to `True`, shears the tree to only include tips present in the feature metadata. If the feature metadata file includes only internal nodes an error is raised. By default this option is set to `False`.

EDIT: Also - will probably update `shear-tree` option to be `shear-to-table` unless anyone has any objections.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a76ebf27a8c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.