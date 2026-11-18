# Issue

**Title:** align step for classify_wf and de_novo_wf function fixed.

## Description

- de_novo_wf function uses the align step so we need to add the new parameters (modifiable by users) used to trim the MSA.
- If skip_gtdb_ref is chosen for de_novo_wf, the Fasttree step will use the .user.msa.fasta file.
- classify_wf function uses the align step so we need to add default value (NON modifiable by users) to the new parameters used to trim the MSA.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9a84ea90f2c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.