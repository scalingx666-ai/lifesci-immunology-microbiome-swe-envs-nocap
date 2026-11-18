# Issue

**Title:** fix keyerr "clade" of cl2ab

## Description

keys of cl2ab is the tuple `(taxstr, taxid)`, thus `cl2ab[clade]` cause the key err

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c13fd8f5e26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.