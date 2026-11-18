# Issue

**Title:** A merge of minor construction branch into read extraction branch

## Description

The happy (?) union of #142 into #139.

- [x] Does this PR change the contracted DBG, catlas, or minhash DB formats?
      If so, merge with care as this will require rebuilding some big files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e41d53789ec1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.