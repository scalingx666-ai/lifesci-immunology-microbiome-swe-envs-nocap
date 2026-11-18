# Issue

**Title:** Fix faith

## Description

In Faith index calculation, the function expected that the rownames are the same as the names found from tree. The linkages are found from rowLinks. Now the rownames are replaced by the links (corresponding node labels from tree).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fdcd5c9dec65`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.