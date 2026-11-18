# Issue

**Title:** getCrossAssociation: assay.type default value

## Description

Currently, `getCrossAssociation` supports calculating correlation between abundance tables, `colData` variables or `dimred`. `assay.type` has default value `"counts"`, however, if `col.var` or `dimred` is used, `assay.type` is not taken into consideration.

I think it would be more clear if user has to decide the assay explicitly. This PR changes the default value of `assay.type` to `NULL`. If nothing is specified, user gets informative error

> Error: One of the following parameters must be specified: 'assay.type1', 'col.var1', 'dimred1'.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2b426a7ffb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.