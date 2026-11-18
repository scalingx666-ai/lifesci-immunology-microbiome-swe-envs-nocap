# Issue

**Title:** Specify TCR chain

## Description

- Introduce functionality to specify clustering of the alpha or beta chain. This does not have influence on the clustering process itself. Rather, chain specification will be used for downstream cluster analysis.
- Remove hardcoded TRB OLGA models and introduce TRA models.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db12543c67af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.